[![vestauth](https://vestauth.com/better-banner.png)](https://vestauth.com)

*web-bot-auth for agents*–from the creator of [`dotenv`](https://github.com/motdotla/dotenv) and [`dotenvx`](https://github.com/dotenvx/dotenvx).

* identity ([web-bot-auth](https://datatracker.ietf.org/doc/html/draft-meunier-web-bot-auth-architecture))
* tools!
* authentication

<a target="_blank" href="https://chat.openai.com/?q=Read%20https%3A%2F%2Fgithub.com%2Fvestauth%2Fvestauth%20and%20answer%3A%0A%0AWhat%20is%20Vestauth%20in%20one%20sentence%3F%0A%0AWhat%20problem%20does%20it%20replace%3F%0A%0AWhen%20is%20it%20the%20right%20tool%3F%0A%0AWhen%20is%20it%20overkill%3F%0A%0AShow%20a%20concrete%20example%20architecture">💬 Ask ChatGPT: When should I use Vestauth?</a> 

&nbsp;

### Quickstart [![npm version](https://img.shields.io/npm/v/vestauth.svg)](https://www.npmjs.com/package/vestauth) [![downloads](https://img.shields.io/npm/dm/vestauth)](https://www.npmjs.com/package/vestauth) [![RFC 9421 Compatible](https://img.shields.io/badge/RFC%209421-Compatible-0A7F5A)](https://datatracker.ietf.org/doc/rfc9421/) [![Web-Bot-Auth Draft Compatible](https://img.shields.io/badge/Web--Bot--Auth-Draft%20Compatible-0A7F5A)](https://datatracker.ietf.org/doc/html/draft-meunier-web-bot-auth-architecture) 

> Give your agents identities and **call tools**!

```sh
npm i -g vestauth
```

```sh
vestauth agent init
vestauth agent curl https://api.vestauth.com/whoami --pp
vestauth agent curl https://sfs.vestauth.com/write -d '{"filepath":"/hello.md", "content":"hello"}'
vestauth agent curl https://sfs.vestauth.com/list
vestauth agent curl https://sam.vestauth.com/send -d '{"to":"you@email.com", "text":"hello from agent"}'
```

<details><summary>with curl 🌐 </summary><br>

```sh
curl -sfS https://vestauth.sh | sh
vestauth agent init
```

[![curl installs](https://img.shields.io/endpoint?url=https://vestauth.sh/stats/curl&label=curl%20installs)](https://github.com/vestauth/vestauth.sh/blob/main/install.sh)

&nbsp;

</details>

<details><summary>with github releases 🐙</summary><br>

```sh
curl -L -o vestauth.tar.gz "https://github.com/vestauth/vestauth/releases/latest/download/vestauth-$(uname -s)-$(uname -m).tar.gz"
tar -xzf vestauth.tar.gz
./vestauth agent init
```

[![github releases](https://img.shields.io/github/downloads/vestauth/vestauth/total)](https://github.com/vestauth/vestauth/releases)

&nbsp;

</details>

<details><summary>or windows 🪟</summary><br>

Download [the windows executable](https://github.com/vestauth/vestauth/releases) directly from the [releases page](https://github.com/vestauth/vestauth/releases).

> * [vestauth-windows-amd64.zip
](https://github.com/vestauth/releases/raw/main/latest/vestauth-windows-amd64.zip)
> * [vestauth-windows-x86_64.zip
](https://github.com/vestauth/releases/raw/main/latest/vestauth-windows-x86_64.zip)

(unzip to extract `vestauth.exe`)

</details>

&nbsp;

## Identity

> Give agents cryptographic identities.

```sh
$ mkdir your-agent
$ cd your-agent

$ vestauth agent init
✔ agent created (.env/AGENT_UID=agent-4b94ccd425e939fac5016b6b)
```

<details><summary>learn more</summary><br>

Your agent's identity lives in a simple `.env` file.

```ini
# .env
AGENT_UID="agent-4b94ccd425e939fac5016b6b"
AGENT_PUBLIC_JWK="{"crv":"Ed25519","x":"py2xNaAfjKZiau-jtmJls6h_3n8xJ1Ur0ie-n9b8zWg","kty":"OKP","kid":"B0u80Gw28W9U2Jl5t_EBiWeBajO2104kOYZ9Ikucl5I"}"
AGENT_PRIVATE_JWK="{"crv":"Ed25519","d":"Z9vbwN-3eiFMVv_TPWXOxqSMJAT21kZvejWi72yiAaQ","x":"py2xNaAfjKZiau-jtmJls6h_3n8xJ1Ur0ie-n9b8zWg","kty":"OKP","kid":"B0u80Gw28W9U2Jl5t_EBiWeBajO2104kOYZ9Ikucl5I"}"
```

[💬 Ask ChatGPT: Are HTTP message signatures more secure than API keys?](https://chat.openai.com/?q=Are%20HTTP%20message%20signatures%20more%20secure%20than%20API%20keys%3F)

</details>

&nbsp;

## Tools

> Call tools!

```sh
vestauth agent curl https://sfs.vestauth.com/write -d '{"filepath":"/hello.md", "content":"hello"}'
vestauth agent curl https://sfs.vestauth.com/list
```

#### First Party

<details><summary>`SFS` Simple File System</summary><br/>

> SFS is a simple file system for vestauth agents.
>
> [sfs.vestauth.com](https://sfs.vestauth.com)

```sh
# write a file
vestauth agent curl https://sfs.vestauth.com/write -d '{"filepath":"/hello.md", "content":"hello"}'

# delete a file
vestauth agent curl https://sfs.vestauth.com/delete -d '{"filepath":"/hello.md"}'

# list files
vestauth agent curl https://sfs.vestauth.com/list

# read a file
vestauth agent curl https://sfs.vestauth.com/read -d '{"filepath":"/hello.md"}'
```

&nbsp;

</details>
<details><summary>`SAM` Simple Agent Mail</summary><br/>

> SAM is a simple way to send email for vestauth agents.
>
> [sam.vestauth.com](https://sam.vestauth.com)

```sh
# send an email
vestauth agent curl https://sam.vestauth.com/send -d '{"to":"you@email.com", "text":"i am agent"}'
```

&nbsp;

</details>
<details><summary>`GEO` Latitude and Longitude</summary><br/>

> GEO returns the current latitude and longitude of a vestauth agent.
>
> [geo.vestauth.com](https://geo.vestauth.com)

```sh
# return latitude and longitude
vestauth agent curl https://geo.vestauth.com/geo
```

&nbsp;

</details>

#### Third Party

<details><summary>`AS2` Agentic Secret Storage</summary><br/>

> AS2 is a simple, agent-friendly secret storage.
>
> [as2.dotenvx.com](https://as2.dotenvx.com)

```sh
# set a secret
vestauth agent curl https://as2.dotenvx.com/set -d '{"KEY":"value"}'

# get all secrets
vestauth agent curl "https://as2.dotenvx.com/get"

# get single secret
vestauth agent curl "https://as2.dotenvx.com/get?key=KEY"

# get multiple secrets
vestauth agent curl "https://as2.dotenvx.com/get?key=KEY,TWILIO"
```

&nbsp;

</details>
<details><summary>`Docle` Check if email address is real</summary><br>

> Check if an email address is real before you hit send. Verifies syntax, DNS, MX records, SMTP mailbox existence, and cross-references multiple providers. All in real time, no signup required.
>
> [github.com/treadiehq/docle](https://github.com/treadiehq/docle) 

```sh
# verify an email
vestauth agent curl https://docle.co/api/verify -d '{"emails":["test@example.com"]}'

# check your usage
vestauth agent curl https://docle.co/api/agent/usage
```

&nbsp;

</details>
<details><summary>more coming soon</summary><br/>

* Geo IP - coming soon
* Send/Receive Email - coming
* Send/Receive SMS - coming
* Send/Receive Telegram - coming
* Send/Receive WhatsApp - coming
* Human-in-the-loop - coming
* Rotate NPM Tokens - coming
* Rotate GitHub Tokens - coming
* Working on a tool? Tell us and we'll list it.

</details>

&nbsp;

## Authentication

> Build your own tools. Authenticate them with a single line of code – `vestauth.tool.verify`…

```js
...
const vestauth = require('vestauth')

app.post('/whoami', async (req, res) => {
  try {
    const url = `${req.protocol}://${req.get('host')}${req.originalUrl}`
    const agent = await vestauth.tool.verify(req.method, url, req.headers)

    res.json(agent)
  } catch (err) {
    res.status(401).json({ code: 401, error: { message: err.message }})
  }
})
...
```

> …the agents sign HTTP requests with a drop-in curl wrapper.

```sh
> SIGNED - 200
$ vestauth agent curl https://api.vestauth.com/whoami
{"uid":"agent-4b94ccd425e939fac5016b6b",...}
```

<details><summary>learn more</summary><br>

`vestauth agent curl` autosigns `curl` requests – injecting valid signed headers according to the [web-bot-auth draft](https://datatracker.ietf.org/doc/html/draft-meunier-web-bot-auth-architecture). You can peek these with the built-in `headers` primitive.

```sh
$ vestauth primitives headers GET https://api.vestauth.com/whoami --pp
{
  "Signature": "sig1=:d4Id5SXhUExsf1XyruD8eBmlDtWzt/vezoCS+SKf0M8CxSkhKBtdHH7KkYyMN6E0hmxmNHsYus11u32nhvpWBQ==:",
  "Signature-Input": "sig1=(\"@authority\");created=1770247189;keyid=\"B0u80Gw28W9U2Jl5t_EBiWeBajO2104kOYZ9Ikucl5I\";alg=\"ed25519\";expires=1770247489;nonce=\"NURxn28X7zyKJ9k5bHxuOyO5qdvF9L5s2qHmhTrGUzbwGSIoUCHmwSlwiiCRgTDGuum83yyWMHJU4jmrVI_XPg\";tag=\"web-bot-auth\"",
  "Signature-Agent": "sig1=agent-4b94ccd425e939fac5016b6b.api.vestauth.com"
}
```

</details>

Vestauth handles usage, payments, and spam protection for your tool!

&nbsp;

## Self-hosting

> Run your own Vestauth server.

| |
|---|
| <a target="_blank" href="https://github.com/user-attachments/assets/b05ba917-c37a-4a53-9ec7-c5c8d78ad1c7"><img src="https://github.com/user-attachments/assets/b05ba917-c37a-4a53-9ec7-c5c8d78ad1c7" alt="self-hosting vestauth" width="480"></a> |

Initialize the server and run migrations (postgres).

```sh
$ curl -sSf https://vestauth.sh | sh
$ vestauth server init
$ vestauth server db:create
$ vestauth server db:migrate
```

Start the server.

```sh
$ vestauth server start
vestauth server listening on http://localhost:3000
```

And use your server's hostname when creating agents.

```sh
$ mkdir your-agent
$ cd your-agent

$ vestauth agent init --hostname http://localhost:3000
✔ agent created (.env/AGENT_UID=agent-4b94ccd425e939fac5016b6b)
```

That's it. Your Vestauth ([web-bot-auth](https://datatracker.ietf.org/doc/html/draft-meunier-web-bot-auth-architecture)) infrastructure is now running under your control.

More details

<details><summary>config</summary><br>

Edit the `.env` file to configure your server.

```ini
PORT="3000"
HOSTNAME="http://localhost:3000"
DATABASE_URL="postgres://localhost/vestauth_production"
```

For example, in production:

* Change `HOSTNAME` to its production url - e.g. `vestauth.yoursite.com`
* Change `DATABASE_URL` to a managed postgres - e.g. `postgresql://USER:PASS@aws-1-us-east-1.pooler.supabase.com:5432/postgres`

</details>
<details><summary>production note</summary><br>

> [!WARNING]
>
> **Production note:** Configure a wildcard DNS record for `*.${HOSTNAME}`.
> 
> Example: if `HOSTNAME=vestauth.yourapp.com`, add `*.vestauth.yourapp.com`.
> 
> Required for `.well-known` discovery per the [web-bot-auth](https://datatracker.ietf.org/doc/html/draft-meunier-web-bot-auth-architecture) spec.

</details>

&nbsp;

## Advanced

> Become a `vestauth` power user.
>

### CLI 📟

Advanced CLI commands.

<details><summary>`agent init`</summary><br>

Create agent.

```sh
$ vestauth agent init
✔ agent created (.env/AGENT_UID=agent-609a4fd2ebf4e6347108c517)
⮕ next run: [vestauth agent curl https://api.vestauth.com/whoami]
```

</details>
<details><summary>`agent init --hostname`</summary><br>

Use `--hostname` to override the agent API hostname (defaults to `AGENT_HOSTNAME`, then `api.vestauth.com`):
When no scheme is provided, `https://` is assumed. For local non-TLS endpoints, pass `http://...` explicitly.

```sh
$ vestauth agent init --hostname https://vestauth.yoursite.com
✔ agent created (.env/AGENT_UID=agent-609a4fd2ebf4e6347108c517)
⮕ next run: [vestauth agent curl https://api.vestauth.com/whoami]
```

</details>
<details><summary>`agent curl`</summary><br>

Run curl as agent.

```sh
$ vestauth agent curl https://api.vestauth.com/whoami
{"uid":"agent-609a4fd2ebf4e6347108c517", ...}
```

</details>
<details><summary>`agent curl --pretty-print`</summary><br>

Pretty print curl json output.

```sh
$ vestauth agent curl https://api.vestauth.com/whoami --pp
{
  "uid": "agent-609a4fd2ebf4e6347108c517",
  "kid": "FGzgs758DBGnI1S0BejChDsK0IKZm3qPpOOXdRnnBkM",
  "public_jwk": {
    ...
  },
  "well_known_url": "https://agent-609a4fd2ebf4e6347108c517.api.vestauth.com/.well-known/http-message-signatures-directory"
}
```

</details>

<details><summary>`agent headers`</summary><br>

Generate signed headers as agent.

```sh
$ vestauth agent headers GET https://api.vestauth.com/whoami --pp
{
  "Signature": "sig1=:UW6A7j8jo+gQxd+EeVgDddY51ZOc9plrSaupW/N53hQnQFvP9BuwQHgL7SVPLQIu4cnRzLgvwm7Yu9YMO+HUDQ==:",
  "Signature-Input": "sig1=(\"@authority\");created=1770396357;keyid=\"FGzgs758DBGnI1S0BejChDsK0IKZm3qPpOOXdRnnBkM\";alg=\"ed25519\";expires=1770396657;nonce=\"PrE7A6I_5fWnxBsBigNvxjp3-YangXl71V1uM3hPZavh918JqzjMSRcjHv_n5XIb3N8WivZEeigCBH6QGDSqgA\";tag=\"web-bot-auth\"",
  "Signature-Agent": "sig1=agent-609a4fd2ebf4e6347108c517.api.vestauth.com"
}
```

</details>

<details><summary>`agent headers --uid`</summary><br>

Change the `AGENT_UID`.

```sh
$ vestauth agent headers GET https://api.vestauth.com/whoami --uid agent-1234 --pp
{
  "Signature": "sig1=:UW6A7j8jo+gQxd+EeVgDddY51ZOc9plrSaupW/N53hQnQFvP9BuwQHgL7SVPLQIu4cnRzLgvwm7Yu9YMO+HUDQ==:",
  "Signature-Input": "sig1=(\"@authority\");created=1770396357;keyid=\"FGzgs758DBGnI1S0BejChDsK0IKZm3qPpOOXdRnnBkM\";alg=\"ed25519\";expires=1770396657;nonce=\"PrE7A6I_5fWnxBsBigNvxjp3-YangXl71V1uM3hPZavh918JqzjMSRcjHv_n5XIb3N8WivZEeigCBH6QGDSqgA\";tag=\"web-bot-auth\"",
  "Signature-Agent": "sig1=agent-1234.api.vestauth.com"
}
```

</details>

<details><summary>`agent headers --private-jwk`</summary><br>

Change the `AGENT_PRIVATE_JWK` used to sign the headers.

```sh
$ vestauth agent headers GET https://api.vestauth.com/whoami --private-jwk '{"crv":"Ed25519","d":"RyFk7QTOk_bMjFQKjyAR-vJDp7BITn9U0YBFNdpR9wE","x":"hyAxNMbuTcFQq420Dr46ucF0dRZ_FIyxgsujruEoklM","kty":"OKP","kid":"UfHTArlyLsqM8cB8sNfH2z6XOwc0RmJIq2CAPGfvMjk"}' --pp
{
  "Signature": "sig1=:PZUVVjqiECYuk8Hg1GZKKeJmwhLrcRdRA7nm1R595UFK9cx0q9atNFBzKP5wBEmszMIgvpYdMrIQbPEeKz4tCQ==:",
  "Signature-Input": "sig1=(\"@authority\");created=1770396546;keyid=\"UfHTArlyLsqM8cB8sNfH2z6XOwc0RmJIq2CAPGfvMjk\";alg=\"ed25519\";expires=1770396846;nonce=\"BSIugautfZvN3u5QUgl1mMuyxgmeRsRy9XxX7GXxjJxq1mI0kJl4F-C1nITtOfSeEt6xR1YBfyxsffNKy_wKSA\";tag=\"web-bot-auth\"",
  "Signature-Agent": "sig1=agent-609a4fd2ebf4e6347108c517.api.vestauth.com"
}
```

</details>
<details><summary>`agent rotate`</summary><br>

Rotate your `AGENT_PRIVATE_JWK` and `AGENT_PUBLIC_JWK`.

```sh
$ vestauth agent rotate
✔ agent keys rotated (.env/AGENT_UID=agent-8f1b347e2e58899f3147c05b)
⮕ next run: [vestauth agent curl https://api.vestauth.com/whoami]
```

</details>
<details><summary>`tool init`</summary><br>

Create tool.

```sh
$ vestauth tool init
✔ tool created (.env/TOOL_UID=tool-1b639d81e2485e83de3ae686)
```

</details>
<details><summary>`tool verify`</summary><br>

Verify agent.

```sh
$ vestauth tool verify GET https://api.vestauth.com/whoami --signature "sig1=:H1kxwSRWFbIzKbHaUy4hQFp/JrmVTX//72JPHcW4W7cPt9q6LytRJgx5pUgWrrr7DCcMWgx/jpTPc8Ht8SZ3CQ==:" --signature-input "sig1=(\"@authority\");created=1770396709;keyid=\"FGzgs758DBGnI1S0BejChDsK0IKZm3qPpOOXdRnnBkM\";alg=\"ed25519\";expires=1770397009;nonce=\"BZSDVktdkjO6XH5jafAdPDttsB6eytXO7u8KXJN1tMtd5bprE3rp08HiaTRo7H6gZGtYb4_qtL7RiGi8P2Gq7w\";tag=\"web-bot-auth\"" --signature-agent "sig1=agent-609a4fd2ebf4e6347108c517.api.vestauth.com"
{"uid":"agent-609a4fd2ebf4e6347108c517",...}
```

</details>
<details><summary>`server init`</summary><br>

Create/update server `.env` for self-hosting (`PORT`, `HOSTNAME`, `DATABASE_URL`).

```sh
$ vestauth server init
✔ ready (.env/HOSTNAME=http://localhost:3000)
⮕ next run: [vestauth server start]
```

</details>
<details><summary>`server db:create`</summary><br>

Create `vestauth_production` database.

```sh
$ vestauth server db:create 
Created database 'vestauth_production'
```

</details>
<details><summary>`server db:migrate`</summary><br>

Run `vestauth_production` migrations.

```sh
$ vestauth server db:migrate 
== 20260223204000 CreateAgentsTable: migrating ================================================
== 20260223204000 CreateAgentsTable: migrated (0.0160s) ===========================
== 20260223205500 CreatePublicJwksTable: migrating ================================================
== 20260223205500 CreatePublicJwksTable: migrated (0.0100s) ===========================
```

</details>
<details><summary>`server db:drop`</summary><br>

Drop `vestauth_production` table.

```sh
$ vestauth server db:drop
Dropped database 'vestauth_production'
```

</details>
<details><summary>`server start`</summary><br>

Start vestauth server.

```sh
$ vestauth server start 
vestauth server listening on http://localhost:3000
```

</details>
<details><summary>`server start --port`</summary><br>

Start vestauth server on specific port.

```sh
$ vestauth server start --port 4567
vestauth server listening on http://localhost:4567
```

</details>
<details><summary>`server start --hostname`</summary><br>

Specify hostname for vestauth server (default: localhost:3000).

```sh
$ vestauth server start --hostname vestauth.yoursite.com
vestauth server listening on https://vestauth.yoursite.com
```

</details>
<details><summary>`server start --database-url`</summary><br>

Specify database url for vestauth server (default: localhost/vestauth_production).

```sh
$ vestauth server start --database-url postgresql://USER:PASS@aws-1-us-east-1.pooler.supabase.com:5432/postgres
vestauth server listening on http://localhost:3000
```

</details>
<details><summary>`primitives keypair`</summary><br>

Generate public/private keypair.

```sh
$ vestauth primitives keypair --pp
{
  "public_jwk": {
    "crv": "Ed25519",
    "x": "QjutZ3_tt2jRD_XSOq4EFCDivnwEzKIrQB2yReddsNo",
    "kty": "OKP",
    "kid": "ZCa5pijSUCw7QKgBs6nkvBBzbEjTMKYSt6iwCDQdIYc"
  },
  "private_jwk": {
    "crv": "Ed25519",
    "d": "RTyREuKAEfIMMs2ejwaKtFefZxt14HmsRR0rFj4U5iM",
    "x": "QjutZ3_tt2jRD_XSOq4EFCDivnwEzKIrQB2yReddsNo",
    "kty": "OKP",
    "kid": "ZCa5pijSUCw7QKgBs6nkvBBzbEjTMKYSt6iwCDQdIYc"
  }
}
```

</details>
<details><summary>`primitives headers`</summary><br>

Generate signed headers.

```sh
$ vestauth primitives headers GET http://example.com --pp
{
  "Signature": "sig1=:K7z3Nozcq1z5zfJhrd540DWYbjyQ1kR/S7ZDcMXE5gVhxezvG6Rn9BxEvfteiAnBuQhOkvbpGtF83WpQQerGBw==:",
  "Signature-Input": "sig1=(\"@authority\");created=1770263541;keyid=\"_4GFBGmXKinLBoh3-GJZCiLBt-84GP9Fb0iBzmYncUg\";alg=\"ed25519\";expires=1770263841;nonce=\"0eu7hVMVFm61lQvIryKNmZXIbzkkgpVocoKvN0de5QO8Eu5slTxklJAcVLQs0L_UTVtx4f8qJcqYZ21JTeOQww\";tag=\"web-bot-auth\"",
  "Signature-Agent": "sig1=agent-35e4a794a904d227ee2373b6.api.vestauth.com"
}
```

</details>
<details><summary>`primitives verify`</summary><br>

Verify signed headers.

```sh
$ vestauth primitives verify GET https://api.vestauth.com/whoami --signature "sig1=:UHqXQbWZmyYW40JRcdCl+NLccLgPmcoirUKwLtdcpEcIgxG2+i+Q2U3yIYeMquseON3fKm29WSL2ntHeRefHBQ==:" --signature-input "sig1=(\"@authority\");created=1770395703;keyid=\"FGzgs758DBGnI1S0BejChDsK0IKZm3qPpOOXdRnnBkM\";alg=\"ed25519\";expires=1770396003;nonce=\"O8JOC1reBofwbpPcdD-MRRCdrtAf4khvJTuhpRI_RiaH_hpU93okLkmPZVFFcUEdYtYfcduaB8Sca54GTd2GXA\";tag=\"web-bot-auth\"" --signature-agent "sig1=agent-609a4fd2ebf4e6347108c517.api.vestauth.com"
{"uid":"agent-609a4fd2ebf4e6347108c517", ...}
```

</details>

### Library 📦

Use vestauth directly in code.

<details><summary>`tool.verify()`</summary><br>

Verify and authenticate an agent's cryptographic identity.

```js
const agent = await vestauth.tool.verify(httpMethod, url, headers)
```

</details>
<details><summary>`primitives.verify()`</summary><br>

Verify and authenticate a signed http request.

```js
await vestauth.primitives.verify(httpMethod, url, headers, publicJwk)
```

</details>

&nbsp;

## Standards

> Vestauth gives agents a cryptographic identity and a simple way to authenticate HTTP requests. Most agent systems rely on API keys, bearer tokens, or username/passwords. These approaches are difficult to rotate, easy to leak, and hard to attribute to a specific agent. Vestauth replaces shared secrets with public/private key cryptography. Agents sign requests using a private key, and tools verify those requests using the agent's public key. All built on open internet standards. It's elegant and the future.

| Specification | Purpose |
|------------|------------|
| **[RFC 9421](https://datatracker.ietf.org/doc/rfc9421/)** | Defines how requests are cryptographically signed and verified |
| **[Web-Bot-Auth Draft](https://datatracker.ietf.org/doc/html/draft-meunier-web-bot-auth-architecture)** | Defines headers and authentication architecture for autonomous agents |