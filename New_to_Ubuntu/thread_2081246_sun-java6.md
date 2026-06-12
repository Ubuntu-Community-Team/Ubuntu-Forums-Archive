---
title: "sun-java6"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by danieljiang on 2012-11-06
Hi!

I want to install the sun-java6, and follow the step as the following:

1.sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
2.sudo apt-get update
3.sudo apt-get install sun-java6-jre sun-java6-plugin
4.sudo update-alternatives --config java


but when I type in the fisrt two lines, the following warning prompts:

W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

what should I deal with it?
Any help will be grateful &#65281;&#65281;

---

### Post by oldos2er on 2012-11-06
Add the key ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
``` although I believe sun-java* has been removed from Ubuntu's repositories due to Oracle's more restrictive license.

---

### Post by Zill on 2012-11-06
danieljiang:  From ["Java Community Documentation"]("https://help.ubuntu.com/community/Java"):
> Oracle (Sun) Java 6 reaches its End of Life in November, 2012. It is not advisable to install Oracle (Sun) Java 6 unless you have some specific need to do so.
It is recommended that users either migrate to OpenJDK, or switch to Oracle Java 7.
The easiest way to install Java/OpenJDK is, IMHO, to install Ubuntu Restricted Extras:
```
sudo apt-get install ubuntu-restricted-extras
```
This package installs support for MP3 playback and decoding, support for various other audio formats (gstreamer plugins), Microsoft fonts, [COLOR="Red"]Java runtime environment[/COLOR], Flash plugin, LAME (to create compressed audio files), and DVD playback.

---

