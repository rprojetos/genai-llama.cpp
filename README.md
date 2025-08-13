# genai-llama.cpp
lab genai llama.cpp

## Instalar dependências
> sudo apt update && sudo apt install -y \
    git build-essential cmake libopenblas-dev libcurl4-openssl-dev

> sudo apt install -y ninja-build

## Clonar o llama.cpp
> cd ~
> git clone https://github.com/ggerganov/llama.cpp

## Compilar com suporte ROCm
O llama.cpp detecta o ROCm automaticamente, mas vamos forçar para garantir:
> cd ~/llama.cpp
> rm -rf build
> cmake -B build -G Ninja -DLLAMA_HIPBLAS=ON -DLLAMA_BUILD_SERVER=ON
> cmake --build build -j$(nproc)

## huggingface-cli com token
Crie um token em: https://huggingface.co/settings/tokens (Scope: “Read”)
No terminal:

> python3 -m pip install -U huggingface_hub
> huggingface-cli login token-gerado-no-huggingface

## baixar modelos
Exemplo:
> huggingface-cli download microsoft/Phi-3-mini-4k-instruct-gguf --local-dir ~/models



