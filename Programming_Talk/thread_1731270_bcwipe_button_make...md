---
title: "bcwipe button make.."
date: 2011-04-17
forum: Programming Talk
---

### Post by oklokl on 2011-04-17
gedit /usr/local/bin/del

```
#!/bin/bash
sudo bcwipe -p *.*
```sudo chmod +x /usr/local/bin/del
button F11 (del)

Please help ..
 Delete a folder or file(Drag the folder or file) ->del-> F11 button


bcwipe-help
option



  -w        disable verificatiobcwipe: invalid option -- '-'
bcwipe version 1.9-8 rev 319 2010-10-04  Copyright 1994-2010 Jetico, Inc.
Usage: bcwipe [OPTIONS]... FILE...
Remove FILE(s) with wiping.
OPTIONS:
  -mb       German BCI/VISTR 7-pass wiping
  -md       U.S. DoD 5220-22M 7-pass extended character rotation wiping
  -me       U.S. DoE 3-pass wiping
  -mf<file> read wiping scheme from file. See *notes below
  -mg       (default) 35-pass wiping by Peter Gutmann
  -ms       7-pass wiping by Bruce Schneier
  -mt       1-pass test mode: fill the start of 512-byte block with block number
  -mz       1-pass zero wiping
  -m N      U.S. DoD 5220-22M N-pass extended character rotation wiping

  -w        disable verification
  -n sec    NAS mode: wait sec seconds between wiping passes. See **notes below
  -s        use ISAAC random instead of SHA-1
 [COLOR=#FF0000] -p        use random pattern instead of full random[/COLOR]
  -r        process the contents directories recursively
  -f        force wiping, never prompt        (use with caution)
  -d        do not delete file(s) after wiping
  -b        wipe contents of block devices    (use with caution)
   -B        disable direct IO access mode for block devices  -t N       use N threads to wipe block devices. Useful for multiple disk devices.   -S        wipe file slacks
[COLOR=#FF0000]  -F        wipe free space on mounted filesystem[/COLOR]
  -i        prompt before any removal (y/[n]/a)
              y - yes, n - no(default), a - yes for all
  -I        disable interactive prompt
  -v        verbose modebcwipe: invalid option -- '-'

---

