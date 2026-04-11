# action-cache-fallback

This repo contains multiple composite actions. The main one in this change is a checkout wrapper at `checkout/action.yml`.

## Checkout action (cache-aware)

Example:

```yaml
- uses: pi-xcels/action-cache-fallback/checkout@<ref>
  with:
    s3-access-key: ${{ secrets.S3_ACCESS_KEY }}
    s3-secret-key: ${{ secrets.S3_SECRET_KEY }}
    # Optional: override the SHA to checkout (40-hex). Defaults to github.sha for the workflow repo.
    sha: ${{ github.sha }}
```

Notes:
- `sha` replaces `ref` (breaking change) and must be a full 40-character SHA-1.
- If you override `repository`, you must also provide `sha`.
- If `cache-key` is omitted, the action uses `pixcels-checkout-<sha>`; `cache-restore-keys` defaults to the same value.
