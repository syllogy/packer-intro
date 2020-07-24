# Packer

Com o Packer instalado, podemos nos aprofundar nele e criar nossa primeira imagem. Nossa primeira imagem será uma Amazon EC2 AMI. Este é apenas um exemplo. O Packger pode criar imagens para múltiplas plataformas.

O Packer pode criar imagens para muitas plataformas diferente da AWS, mas a AWS não querer software adicional instalado no seu computador e seu nível gratuito o torna gratuito para a maioria das pessoas. É por isso que escolhemos usar a AWS como exemplo. Se você não se sentir à vontade para configurar uma conta da AWS, sinta-se à vontade para seguir em frente, pois os princípios básicos também se aplicam a outras plataformas.

## Modelo

O arquivo de configuração usado para definir qual imagem querer construir e como é chamado de modelo na terminologia do Packer. 

O formato de um modelo é JSON simples. O JSON alcançou o melhor equilíbrio entre editável por seres humanos e editável por máquina, permitindo que modelos feitos à mão e modelos gerados por máquina sejam facilmente criados.

Este é um modelo básico pronto para uso. Ele deve ser imediatamente reconhecido como um objeto JSON básico e normal.

entro do objeto, a builders seção contém uma matriz de objetos JSON configurando um construtor específico . Um construtor é um componente do Packer responsável por criar uma máquina e transformá-la em uma imagem.

```bash
packer validate instance.json
```

```bash
packer build \
    -var 'aws_access_key=YOUR ACCESS KEY' \
    -var 'aws_secret_key=YOUR SECRET KEY' \
    instance.json
```

É relativamente simples subir uma nova instância em um dos provedores de nuvem como AWS, Azure, Digital Ocean (entre outros). No entando, não basta apenas subir uma instância pois precisamos também provisionar (instalar) e preparar essa máquina virtualizada.

Ideal seria cria uma imagem que já está tuda provisionada com o software para depois subir a máquina na nuvem baseada nela. Exatamente essa é a tarefa do Packer, uma ferramenta da área de Infraestrutura como Código com a qual podemos definir todos os passos de instação declarativamente (em um arquivo json) e aplicar no provedor de nuvem que desejarmos.
