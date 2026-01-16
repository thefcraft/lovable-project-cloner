# Lovable Project Cloner

A simple script to download source code from Lovable.dev projects to your local machine. It handles the API requests, decodes binary files, and reconstructs the directory structure automatically.

### Installation

**Using uv:**
```bash
uv sync
```

**Using pip:**
```bash
pip install aiohttp pydantic-settings python-dotenv
```

### Authentication

The script requires a `BEARER_TOKEN`. You can provide this in two ways:

1. **Terminal:** `export BEARER_TOKEN="Bearer your_token_here"`
2. **.env file:** Create a `.env` file in the root directory and add `BEARER_TOKEN="Bearer your_token_here"`

**How to find your token:** 
1. Open any project on Lovable.
2. Open Browser DevTools (F12) -> **Network** tab.
3. Refresh the page and click on a request to `api.lovable.dev`.
4. Copy the value of the `authorization` request header.

### Usage

```bash
# Using uv
uv run main.py <lovable-project-url>

# Using python directly
python main.py <lovable-project-url>
```

**Options:**
- `--force`: Overwrite the project folder if it already exists locally.
- Projects are saved in the `./projects/` directory, named by their unique ID.

### Development Note
If you are using `uv` and want to enable local caching of API responses, the `dev` dependency group includes `aiohttp-client-cache`. To use it, set `AIOHTTP_CACHE_DIR` in your environment or `.env` file.