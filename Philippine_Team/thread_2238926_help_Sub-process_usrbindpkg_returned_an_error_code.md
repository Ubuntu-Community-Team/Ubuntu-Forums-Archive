---
title: "help Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2014-08-11
forum: Philippine Team
---

### Post by alhrby26 on 2014-08-11
[COLOR=#333333][FONT=monospace]sudo apt-get install -f[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Building dependency tree[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Reading state information... Done[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Correcting dependencies... Done[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]The following packages were automatically installed and are no longer required:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]  chromium-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]codecs-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]ffmpeg-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]extra wine-gecko2.24 wine-gecko2.24:i386[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]  wine-mono4.5.2[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Use 'apt-get autoremove' to remove them.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]The following extra packages will be installed:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]  wine1.6-amd64[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]The following NEW packages will be installed:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]  wine1.6-amd64[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]2 not fully installed or removed.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Need to get 0 B/15.9 MB of archives.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]After this operation, 123 MB of additional disk space will be used.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Do you want to continue? [Y/n] y[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace](Reading database ... 175219 files and directories currently installed.)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Preparing to unpack .../wine1.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]6-amd64_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]1%3a1.6.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]2-0ubuntu4_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64.deb ...[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Unpacking wine1.6-amd64 (1:1.6.2-0ubuntu4) ...[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]2dpkg-deb (subprocess): cannot copy archive member from '/var/cache/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]apt/archives/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]wine1.6-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64_1%[/FONT][/COLOR][COLOR=#333333][FONT=monospace]3a1.6.2-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0ubuntu4_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64.deb' to decompressor pipe: failed to read (Input/output error)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]dpkg-deb (subprocess): decompressing archive member: lzma error: unexpected end of input[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]dpkg-deb: error: subprocess <decompress> returned error exit status 2[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]dpkg: error processing archive /var/cache/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]apt/archives/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]wine1.6-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64_1%[/FONT][/COLOR][COLOR=#333333][FONT=monospace]3a1.6.2-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0ubuntu4_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64.deb (--unpack):[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace] cannot copy extracted data for './usr/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]lib/x86_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]64-linux-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]gnu/wine/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]oleaut32.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]dll.so' to '/usr/lib/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]x86_64-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]linux-gnu/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]wine/oleaut32.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]dll.so.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]dpkg-new'[/FONT][/COLOR][COLOR=#333333][FONT=monospace]: unexpected end of file or stream[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Errors were encountered while processing:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace] /var/cache/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]apt/archives/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]wine1.6-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64_1%[/FONT][/COLOR][COLOR=#333333][FONT=monospace]3a1.6.2-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0ubuntu4_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64.deb[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT][/COLOR]

---

### Post by ian-weisser on 2014-08-11
The dpkg error seems clear: 

> **alhrby26 said:**
> ```

[COLOR=#333333][FONT=monospace]Unpacking wine1.6-amd64 (1:1.6.2-0ubuntu4) ...[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]2dpkg-deb (subprocess): cannot copy archive member from '**/var/cache/**[/FONT][/COLOR]**[COLOR=#333333][FONT=monospace]apt/archives/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]wine1.6-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64_1%[/FONT][/COLOR][COLOR=#333333][FONT=monospace]3a1.6.2-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0ubuntu4_[/FONT][/COLOR]**[COLOR=#333333][FONT=monospace]**amd64.deb**' to decompressor pipe: failed to read (Input/output error)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]dpkg-deb (subprocess): decompressing archive member: lzma error: **unexpected end of input**[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]dpkg-deb: error: subprocess <decompress> returned error exit status 2[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]dpkg: error processing archive /var/cache/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]apt/archives/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]wine1.6-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64_1%[/FONT][/COLOR][COLOR=#333333][FONT=monospace]3a1.6.2-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]0ubuntu4_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64.deb (--unpack):[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace] cannot copy extracted data for './usr/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]lib/x86_[/FONT][/COLOR][COLOR=#333333][FONT=monospace]64-linux-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]gnu/wine/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]oleaut32.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]dll.so' to '/usr/lib/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]x86_64-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]linux-gnu/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]wine/oleaut32.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]dll.so.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]dpkg-new'[/FONT][/COLOR][COLOR=#333333][FONT=monospace]: **unexpected end of file or stream**[/FONT][/COLOR]
```

The system is saying "Hey, this is incomplete." The package wine1.6-amd64 is corrupt or incomplete.
Stop trying to install the broken package. Delete it from your cache and let the package manager download a fresh (complete) copy.

Delete the broken package using the command:
```
sudo rm [COLOR=#333333][FONT=monospace]/var/cache/apt/archives/wine1.6-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]amd64_1%[/FONT][/COLOR][COLOR=#333333][FONT=monospace]3a1.6.2-0ubuntu4_amd64.deb[/FONT][/COLOR]
```

---

### Post by alhrby26 on 2014-08-11
Thank you

---

