---
title: "Why does this nautilus script not work?"
date: 2010-08-12
forum: Programming Talk
---

### Post by conjunctivitis on 2010-08-12
Hello,

I'm using 10.04 and I'm looking for a convenient context menu printing script.  I'm a musician and I often have to print large batches of pdfs.  I found this script on [http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus](http://www.frenssen.be/content/printing-file-right-click-context-menu-nautilus) and followed the instructions explicitly (it's in the /.gnome2/nautilus-scripts folder and I made it executable with chmod +x), but it doesn't seem to do anything at all when i run it.  Can you help me troubleshoot or point me in the right direction?  Thanks

Dan


#!/bin/bash

# print.sh

# print files from the right-click context menu in Nautilus.
# place this script in ~/.gnome2/nautilus-scripts


# the printer to use (as shown in the Printer Configuration gui or in /etc/cups/printers.conf)
printer=Samsung ML-1640 Series

echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | while read file
	do
		lpr -P "$printer" "$file"
done
exit 0

---

### Post by MadCow108 on 2010-08-13
this seems wrong:
printer=Samsung ML-1640 Series

you need to quote the printer name in bash:
printer="Samsung ML-1640 Series"

---

### Post by conjunctivitis on 2010-08-13
I already tried that.  Same result--that is--no result.  I don't even know how to debug since running nautilus from the console doesn't offer me the print.sh script...

---

