# http-stt

Hermes STT plugin — transcribes audio via any HTTP speech-to-text service (local or remote).

## Install

```bash
git clone https://github.com/seamusmore/hermes-http-stt.git ~/.hermes/plugins/http-stt
```

Then restart the Hermes gateway.

## Configure

Add to `~/.hermes/config.yaml`:

```yaml
stt:
  enabled: true
  provider: http_stt
  http_stt:
    service_url: http://your-stt-service:port
    language: auto
```

- **`service_url`** — required. Your STT service URL (no trailing slash).
- **`language`** — optional, defaults to `auto`.

## How it works

The plugin registers a `TranscriptionProvider` named `http_stt`. When the gateway receives a voice message, it POSTs the audio file to `{service_url}/transcribe` and expects a JSON response:

```json
{"transcript": "recognized text", "text": "alternative field"}
```

## STT service example

See [hermes-stt-service](https://github.com/seamusmore/hermes-stt-service) for a ready-to-run SenseVoice STT service.

## License

MIT
