---
title: "[SOLVED] installation issue vmd in ubuntu 8.041 lts"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by MRM0607 on 2008-10-13
Dear ubuntu users,

I am trying to install VMD software on ubuntu 8.041 lts.

After installation when I type VMD, a window breifly flashes and disappears.

VMD binary is static bound. While comparing libs it require I found following differences from the suggested structure (differences are highlighted below)

mamta@requiem:~$ ldd /usr/local/lib/vmd/vmd_LINUX
	linux-gate.so.1 =>  (0xb7f8e000)
	libGL.so.1 => /usr/lib/libGL.so.1 (0xb7f1f000)
	libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7e9c000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7e83000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7d9c000)
	libXft.so.2 => /usr/lib/libXft.so.2 (0xb7d8a000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7d86000)
	libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb7d82000)
	[COLOR="DarkRed"]libstdc++.so.5 => not found[/COLOR]
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7d5c000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7d51000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c02000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb7bf4000)
	libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0xb7bef000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb7beb000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb7be6000)
	libdrm.so.2 => /usr/lib/libdrm.so.2 (0xb7bdc000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7ae9000)
	[COLOR="DarkRed"]/lib/ld-linux.so.2 (0xb7f8f000)[/COLOR]
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb7ae7000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb7ace000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb7aa4000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7a37000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb7a22000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7a1a000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb7a16000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb7a11000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb79f0000)

A search result shows me that these files are present in 

[COLOR="DarkRed"][/COLOR] /user/lib/libstdc++.so.5
usr/lib/debug/ld-linux.so.2

Could somebody please suggest how to remedy this situation.

Thank you.
mrm0607

[COLOR="DarkRed"]The issue I was able to resolve by installing package ]libstdc++5 ( for - libstdc++.so.5)and package libc6 (for - lib/ld-linux.so.2)[/COLOR], [COLOR="DarkRed"]commands are listed below

sudo apt-get install libstdc++5
sudo apt-get install libc6

The issue cropped up because static bind was calling libstdcc++.so.5 which was not present. Installation of the above mention lib took care of the issue.

Thank you.
mrm0607[/COLOR]

---

