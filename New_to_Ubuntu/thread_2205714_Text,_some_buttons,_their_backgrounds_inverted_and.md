---
title: "Text, some buttons, their backgrounds inverted and illegible"
date: 2014-02-15
forum: New to Ubuntu
---

### Post by andy36 on 2014-02-15
I am new to ubuntu (13.10) and am experiencing an intermittent problem with how text displays. I am having great difficulty even coming up with sensible search terms to look for a solution. This "inline attachment" is a screen capture showing what the problem looks like:

[ATTACH=CONFIG]250366[/ATTACH]

When everything is displaying correctly, the icon labels are grey on a white background, there is no orange box around the search pane, and the window title and buttons to close/minimize do not have green borders. Sometimes I can restart and the problem goes away. Sometimes not. When the problem is happening, it shows up in every window or program I run--all of the "program" text is garbled like this (menus, toolbars, icons, tabs, ...), but text that is generated as html or whatever (websites) seems to appear okay.

As I said, this is ubuntu 13.10 64-bit. Other possibly relevant things... The processor is intel core i5 with no graphics card, just the native graphics. I have tried running something called the Intel Graphics Installer from the "Intel Open Source Technology Center," but the installer crashes when "Listing Packages" and throws this error:
> [INDENT]Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/aptdaemon/worker.py", line 323, in _process_transaction
    self.query(trans)
  File "/usr/lib/python3/dist-packages/aptdaemon/pkcompat.py", line 2132, in query
    self.get_packages(trans, **trans.kwargs)
  File "/usr/lib/python3/dist-packages/aptdaemon/pkcompat.py", line 2565, in get_packages
    self._emit_package(trans, pkg)
  File "/usr/lib/python3/dist-packages/aptdaemon/pkcompat.py", line 2845, in _emit_package
    self._emit_pkg_version(trans, pkg.installed, info)
  File "/usr/lib/python3/dist-packages/aptdaemon/pkcompat.py", line 2864, in _emit_pkg_version
    trans.emit_package(info, id, version.summary)
  File "/usr/lib/python3/dist-packages/apt/package.py", line 333, in summary
    return self._translated_records.short_desc
UnicodeDecodeError: 'utf-8' codec can't decode byte 0x92 in position 579: invalid start byte
[/INDENT]


Anybody have a link to a solution for this?

---

### Post by Vladlenin5000 on 2014-02-15
What is your graphics card? Have you installed proprietary drivers?

---

### Post by andy36 on 2014-02-15
No graphics card. Intel core i5 processor's native graphics. I tried to install drivers as described above, but it doesn't work. The only proprietary drivers I'm using are broadcomm something-or-another for my wireless card.

Settings --> Details --> Graphics says, "Driver Intel(R) Haswell Desktop Experience Standard." As far as I know, I did not install that.

The broadcom driver is 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary). Probably not affecting the video.

---

### Post by andy36 on 2014-02-15
lspci | grep VGA...


00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)

---

### Post by andy36 on 2014-02-16
Is there anything I can do the next time this happens that would help someone figure out what the problem is? Save some logfile? Run sudo something-or-another?

---

### Post by Echoloc8 on 2014-03-27
I am getting the exact same error when I try to run the intel graphics installer. 

Here's my lspci output:

00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)

Would love to know what the fix is for this one. Google's only really useful result is this thread.

-Rich

---

