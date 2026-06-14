# lcdctl - QNAP TS-853A LCD Controller

Control the front-panel LCD on QNAP TS-853A (and similar models) running Linux.

The LCD serial port is `/dev/ttyS1` at 1200 baud.

Requires `pyserial`:
```bash
sudo apt install python3-serial
# or: pip3 install -r requirements.txt
```

Run as root - the LCD serial device needs write access:
```bash
sudo ./lcdctl main
```

## Commands

| Command | Description |
|---------|-------------|
| `main` | Show hostname, disk % and memory usage |
| `main --disk /path` | Same as above, disk usage for a specific path |
| `static "text" "text"` | Write static text to row 0 and row 1 |
| `static --line0 "text" --line1 "text"` | Same with flags |
| `scroll "text"` | Scroll long text across a row |
| `stats` | Auto-cycle system stats (hostname, uptime, load, memory, disk, CPU temp) |
| `demo` | Run a demo of all features |
| `clear` | Blank the LCD |
| `on` | Enable LCD backlight |
| `off` | Disable LCD backlight |

## Systemd Service

```bash
sudo cp lcdctl.service /etc/systemd/system/
sudo systemctl daemon-reload
sudo systemctl enable --now lcdctl
```

## Credits

The low-level serial protocol implementation is based on [bkram/qnapdisplay](https://github.com/bkram/qnapdisplay).
