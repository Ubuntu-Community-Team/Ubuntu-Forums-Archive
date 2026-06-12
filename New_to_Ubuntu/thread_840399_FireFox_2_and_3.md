---
title: "FireFox 2 and 3"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by rockinlinux on 2008-06-25
I do a lot of web development and was wondering if there is a way i can run both firefox 2 and 3. I have googled around but not found much. thanks for any help and thanks for your time!

---

### Post by DM was on fire! on 2008-06-25
I have Firefox 2.0 on Linux, and Firefox 3.0 installed in Wine, but there's a huge different between the two (back when I was running 2.0 on both).
Sadly, that's really the only I can think of, with the exclusion of maybe have multiple accounts and updating one Firefox to run 3.0 and one to run 2.0. :)

---

### Post by bilbo.san on 2008-06-25
I actually needed the same thing... but I have given up. Perhaps what DM says could work.
The only choice I had was to stick with FF2 on my windows machine and use FF3 on Linux. Something that I noticed is that FF3 starts up much slower on Windows than the previous version.

---

### Post by Greyed on 2008-06-25
I'd say install a copy of FF2 from a Mozilla archive.  Then have different profiles for each since flipping between FF2 and FF3 is problematic.  This way FF3 is updated normally $apt-flavor-you-use while FF2 is still available when you need it.

---

### Post by acidsolution on 2008-06-25
Firefox 3 can be directly started without installing it in linux 
so u can install ff2 on your PC and keep the files for FF3 
whenever you want to start FF3. just navigate through the folder of FF3 and than 
run 
```

./firefox3-bin

```
I am not sure with the file name 
you can download FF3 from 

[http://rebecka.jiddernet.se/firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2](http://rebecka.jiddernet.se/firefox/releases/3.0/linux-i686/en-US/firefox-3.0.tar.bz2)

I am not sure but I think this might help you .

---

### Post by stchman on 2008-06-25
> **rockinlinux said:**
> I do a lot of web development and was wondering if there is a way i can run both firefox 2 and 3. I have googled around but not found much. thanks for any help and thanks for your time!

There is no need to have both.  FF3 is WAAAAYYYY better then FF2 IMO.

If you must run FF2 then you can download the FF2 2.0.0.14 tar.gz pre-compiled binary.  This is not source, you ahve to go to the

Get it here.
[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.14/linux-i686/en-US/firefox-2.0.0.14.tar.gz](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.14/linux-i686/en-US/firefox-2.0.0.14.tar.gz)

You can then decompress it in say your /opt folder.

After that you can run a command like this.  
```
/opt/firefox/firefox
```

I recommend that you do this in another account as you don't want the two ~/.mozilla profiles mixing it up.

---

### Post by rockinlinux on 2008-06-25
> **stchman said:**
> There is no need to have both.  FF3 is WAAAAYYYY better then FF2 IMO.

If you must run FF2 then you can download the FF2 2.0.0.14 tar.gz pre-compiled binary.  This is not source, you ahve to go to the

Get it here.
[http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.14/linux-i686/en-US/firefox-2.0.0.14.tar.gz](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.14/linux-i686/en-US/firefox-2.0.0.14.tar.gz)

You can then decompress it in say your /opt folder.

After that you can run a command like this.  
```
/opt/firefox/firefox
```

I recommend that you do this in another account as you don't want the two ~/.mozilla profiles mixing it up.
 

Yeah it is but for WEB DEVELOPMENT you need to test.

Anyway i found out that simply by extracting the tar ball you can run the "firfox" and it will open FF3. you cannot however run FF2 and FF3 at the same time but its easy to have both on a linux box. And for those of you running it under wine...try a VM :)

---

### Post by nanotube on 2008-06-25
> **rockinlinux said:**
> you cannot however run FF2 and FF3 at the same time ...

actually, you can, with the help of the "-no-remote" cli argument to firefox. here's what you do:

run firefox2 "regularly".

then, start firefox3 as:
```
/path/to/firefox3 -ProfileManager -no-remote
```
in profilemanager, create a new fresh profile to use for firefox3.

from then on, start firefox3 as
```
/path/to/firefox3 -P yourff3profile -no-remote
```

and you'll be able to run both at the same time.

(if ff3 is your default, and you're 'adding' ff2, then just 
```
s/firefox3/firefox2/
``` in all the above

it's better to run both with "-no-remote", so that neither one tries to attach to a running instance of the other.

in summary: 
1. run your firefoxes with -no-remote so that they can run at the same time
2. run each of them with a separate profile, otherwise one will barf up the other's profile

hope that helps. ;)

---

### Post by rockinlinux on 2008-06-26
coo, thanks :) i will give it a whirl. when you say profile do you mean user account? any way to get menu links?

---

### Post by nanotube on 2008-06-26
> **rockinlinux said:**
> coo, thanks :) i will give it a whirl. when you say profile do you mean user account? any way to get menu links?

by profile i mean the firefox profile, not a whole different user account. the firefox profile is located in ~/.mozilla, and it is possible to have several distinct profiles in there if you have firefox create them.

---

