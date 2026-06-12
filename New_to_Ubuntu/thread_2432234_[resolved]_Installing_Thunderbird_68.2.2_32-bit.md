---
title: "[resolved] Installing Thunderbird 68.2.2 32-bit"
date: 2019-11-29
forum: New to Ubuntu
---

### Post by nginmu on 2019-11-29
I have a portable USB HDD with my Thunderbird profile on it. Windows PC running Thunderbird 68.2.2 32-bit release update channel will access the profile on the HDD successfully if I invoke Thunderbird with the appropriate command line options.

On my Lubuntu machine (showing in sytem information as Ubuntu 18.04.3 LTS), the latest version of Thunderbird I can find in synaptic is 68.2.1

I tried updating the repositories & manually running apt-get update but could still only see 68.2.1

When trying to access my profile using Thunderbird 68.2.1, I get an error message saying my profile is too new to be loaded by this older version of Thunderbird.

I found a copy of thunderbird-68.2.2.tar.bz2 on the mozilla website but when I tried to install it things got messy.

Extracting the archive seemed to go okay:

```

cd /home/me/Downloads
tar -jxvf thunderbird-68.2.2.tar.bz2

```

- gave me a folder 'thunderbird' full of files

But then, the instructions I was following 

```

./configure
make
make install

```

seemed to be wide of the mark, starting with an error "./configure - no such directory" (or something similar)

Looking inside the extracted archive, it does look like the right sort of files to be using make, make install aren't there. So I think I'm trying to go about installing this the wrong way?

Any pointers gratefully received.

(anything really that will allow me to get thunderbird running on my lubuntu box such that it will successfully load my external profile from the USB HDD)


[resolved]

- discovered there is no installation necessary beyond unpacking the tar archive. I guess I will just hang in there with the 68.2.2 operating directly from the extraction directory, invoking it from a suitable command line to cause it to load the HDD profile. And just wait until the repositories catch up.

---

### Post by Impavidus on 2019-11-29
From the [release notes]("https://www.thunderbird.net/en-US/thunderbird/68.2.2/releasenotes/"):> Thunderbird version 68.2.2 is a follow-up to version 68.2.1 to fix an upgrade problem.

Then [sic] upgrading a 64bit version of Thunderbird version 60 to version 68,  the existing profile wasn't recognized and a new profile was created.
 Note: If your profile is still not recognized, select it by visiting about:profiles in the Troubleshooting Information.

It seems that was the only change, so the 32 bit version of Thunderbird 68.2.2 is identical to 68.2.1. Maybe some people didn't see the point of pushing a new version to the repositories, but this causes Thunderbird to think (incorrectly) that the profile belongs to a newer, incompatible version. There should be a file somewhere in the profile telling for which version it was made. Changing this file to match version 68.2.1 should fix the problem, but it's inconvenient to do so every time you move the profile from your Windows box to your Lubuntu box.

---

