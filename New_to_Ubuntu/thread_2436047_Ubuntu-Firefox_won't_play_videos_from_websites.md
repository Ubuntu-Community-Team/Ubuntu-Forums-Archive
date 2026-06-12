---
title: "Ubuntu-Firefox won't play videos from websites"
date: 2020-01-30
forum: New to Ubuntu
---

### Post by wild-lovely-one on 2020-01-30
Hi 
Just out of the cocoon.

I am trying to watch videos online, but get either an error message (no compatible source was found for this media)( media_err_src_not_supported ) or I get an image instead of the video player, on the webpage, with this message-Error loading player: No playable sources found
Youtube works just fine, but not other web pages.
On windows I never had this problem.
Help please
thxs

Video Card is -    :02.0 VGA compatible controller: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display (rev 0e)

---

### Post by Frogs Hair on 2020-01-30
Hello and Welcome !

You can start by installing the following codec packages. Copy and paste the command in the terminal and enter your password. Make sure DRM content is enabled in Firefox settings as well , just enter settings and search DRM. 

```
sudo apt install ubuntu-restricted-extras
```

---

### Post by SeijiSensei on 2020-01-30
Also make sure the Widevine add-on from Google is installed and activated. (It usually comes along with Firefox.) Choose Add-Ons from the main Firefox menu. 

Also some sites still rely on Adobe Flash.  You can add it to your browser with
```

sudo apt update
sudo apt install flashplugin-installer

```
It cannot be shipped with Ubuntu because it is not free.

It would make it much easier to diagnose the problem if you posted a URL that does not work.

---

### Post by NM5TF on 2020-02-01
I have shockwave-flash in my add-ons...along with Widevine and the OpenH264 codec installed by Firefox...

and there is also this.....use it at your own risk it says.....maybe not a good idea, but maybe a last resort...

[https://support.mozilla.org/en-US/kb/flash-blocklists](https://support.mozilla.org/en-US/kb/flash-blocklists)

---

### Post by richard378 on 2020-02-02
In Firefox Preferences scroll to the bottom of General Settings and enable DRM.  It is required for many websites and is not enabled by default.  This will allow you to watch the videos and pictures you can't normally see on websites that require additional codecs.  It is usually the problem when you can't view things on the internet in Firefox.

---

### Post by dan3712 on 2020-02-11
@Frogs Hair
I had this same issue, and this did the trick. Thanks!

---

