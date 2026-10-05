# Universal Data Converter & CRC Tool

A single-page, browser-only tool for converting byte data between formats and computing checksums and CRCs. No server, no build step, no dependencies. Everything runs locally in your browser, so no data ever leaves your machine.

**Live site:** https://venu-konda.github.io/data-converter-crc/

## Features

### Conversions
Paste data in any one of these formats and see it in all the others at once:

- Hex (spaced, continuous, `0x`-prefixed, or as a C array)
- Decimal (unsigned 0–255 or signed -128..127)
- Octal
- Binary
- Base64 (standard and URL-safe)
- ASCII / UTF-8 text (control bytes are shown as `\xNN`)
- Reversed byte order and bit-reversed bytes

Click any output box to copy it to the clipboard.

### Numeric views
- Data length in bytes and bits
- Unsigned and signed 8-bit values
- 16/32/64-bit integers and IEEE 754 float32/float64, in both big-endian and little-endian
- All 16-bit and 32-bit words in the data, with selectable byte order

### Simple checksums
- Sum-8 (mod 256) and two's-complement checksum
- XOR-8 (LRC / BCC)
- Sum-16 (mod 65536)
- Fletcher-16
- Adler-32

### CRC
- Catalog of common algorithms: CRC-8 (SMBus, MAXIM, SAE-J1850), CRC-16 (CCITT-FALSE/CCSDS, XMODEM, KERMIT, X-25, ARC, MODBUS, USB, DNP), CRC-32 (ISO-HDLC/zlib, Castagnoli, BZIP2, MPEG-2, JAMCRC, POSIX)
- Custom CRC: any width from 8 to 32 bits with your own polynomial, init, XOR-out, and reflect-in/out settings
- CRC result shown as hex, decimal, binary, and as bytes in both byte orders
- **Append mode:** produces "Data + CRC" in hex and Base64, ready to send
- **Verify mode:** tick "CRC is already appended to input" to check a received frame. The tool reports a match, a mismatch, or a match in the other byte order
- Built-in self-test runs every catalog algorithm against the standard check value `"123456789"`

## Usage

1. Open the live site, or open `index.html` directly in any modern browser.
2. Pick the input format, paste or type the data, or use **Load file…** to read raw bytes from a file.
3. Results update as you type. Press `Ctrl+Enter` (or `Cmd+Enter`) to convert manually if auto-convert is off.
4. Choose a CRC algorithm and the byte order you need for append or verify.

Accepted separators for numeric input: space, comma, semicolon, colon, newline. Hex may also be one continuous string.

## Running locally or offline

The whole tool is the single file `index.html`. Download it and double-click it, or keep a copy on a shared drive. It works with no network connection.

## Updating the site

The site is served by GitHub Pages from the `main` branch of this repository. To publish a change, edit `index.html` and push to `main`. GitHub rebuilds the site automatically, usually within a minute.

## Hosting and availability

GitHub Pages has no expiry date. The site stays online for as long as this repository exists, remains public, and the owning account is active. There is nothing to renew.

GitHub applies soft usage limits to Pages sites (100 GB bandwidth per month, 1 GB site size), which a single 20 KB page will never approach.

## Browser support

Any current version of Chrome, Edge, Firefox, or Safari. The tool uses standard Web APIs only (`TextEncoder`, `DataView`, `BigInt`, Clipboard API).

## License

MIT. See [LICENSE](LICENSE).
