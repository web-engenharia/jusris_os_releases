# jusris_os_releases

Canal público de **distribuição do executável JusrisOS** e do **feed de atualização assinado**.

> ⚠️ Este repositório **não contém código-fonte** — apenas binários de release,
> manifestos de atualização e a chave pública de verificação. O software é
> proprietário e rege-se pela Licença JusrisOS (aceita na instalação).

## O que vive aqui

- **GitHub Releases** (por tag `vX.Y.Z`): binários do executável desktop por
  plataforma (`linux-x86_64`, `win-x86_64`, `mac-aarch64`);
- **`updates/` (feed estável via GitHub Pages)**:
  - `updates/manifest.json` — feed que o app consulta;
  - `updates/manifest.json.sig` — assinatura Ed25519 dos bytes exatos do manifest;
  - `updates/updates_ed25519.pub` — chave pública de verificação.

URL do feed (após habilitar Pages):

```
https://web-engenharia.github.io/jusris_os_releases/updates/manifest.json
```

## Como o app usa

Configuração do desktop (env):

```bash
UPDATES_URL=https://web-engenharia.github.io/jusris_os_releases
UPDATES_PUBLIC_KEY_FILE=/caminho/updates_ed25519.pub   # ou UPDATES_PUBLIC_KEY=<base64>
```

Fluxo: `manifest.json` (assinatura validada) → artefato (`sha256` conferido) →
swap com backup + rollback (launcher). Trial de 3 dias por versão: cada nova
release renova o período de avaliação; expirado, o app se auto-bloqueia.

## Publicar uma release

O processo completo (build por plataforma, assinatura e publicação do feed) é
executado pelo pipeline no repositório **privado** do código, que empurra
artefatos e feed para cá — veja o guia de releases no repo do projeto.
# jusris_os_releases
