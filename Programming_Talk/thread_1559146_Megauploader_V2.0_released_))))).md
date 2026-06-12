---
title: "Megauploader V2.0 released :)))))"
date: 2010-08-23
forum: Programming Talk
---

### Post by hakermania on 2010-08-23
Ok, so this is a program for easy-uploading to Megaupload.com.
It uses Plowshare, a tool for easy uploading-downloading from a lot of hosters! As you know, Ubuntu is not known for its Flash, and Megaupload uses flash for uploading... So, I decided to make this program that co-operates with Plowshhare...
It supports Single File Uploading, MultiFile Uploading, All Files in Folder Uploading and Files With Different Description Uploading.


The funny is that it uploaded itself to megaupload xD 
Download Link:**[COLOR=Red][http://www.megaupload.com/?d=ZTL7E2H5](http://www.megaupload.com/?d=ZTL7E2H5)[/COLOR]**
It has as dependencies the recode and curl packages, so it will be asked to be installed :)

):P):P):P):P
Waiting for comments and suggestions ;)

---

### Post by brad_c6 on 2010-08-23
Nice Job!:D
(What do ya think as far as making a Deb?)

---

### Post by hakermania on 2010-08-23
Well, making a DEB package is a nice idea, but I have to put things into the $USER folder. i had an issue here for this:
[http://ubuntuforums.org/showthread.php?p=9726773](http://ubuntuforums.org/showthread.php?p=9726773)
but I really didn't got any replies...So Idk how to place files into the USER folder with the use of a DEB package... If you could help me on this...

---

### Post by hakermania on 2010-08-23
As you can see I can't still find an answer on this issue...

---

### Post by Rany Albeg on 2010-08-23
Good Job!
This is very satisfying to program something you'll use afterwards, and I'm very happy for you!

Very nice work.

---

### Post by hakermania on 2010-08-23
Hehe, thank you!

---

### Post by Bachstelze on 2010-08-23
> **hakermania said:**
> 
but I really didn't got any replies...So Idk how to place files into the USER folder with the use of a DEB package... If you could help me on this...

You don't.  If a user does not want to use your program, that would pollute his home directory unnecessarily.  Make your program create them on first start.

---

### Post by KdotJ on 2010-08-23
> **Bachstelze said:**
> You don't.  If a user does not want to use your program, that would pollute his home directory unnecessarily.  Make your program create them on first start.

Is this the preferred standard? I have in the past made simple bash scripts which execute at .deb install just to save on code in my program (code which may only be ever executed once). Maybe I'll rethink in the future lol

---

### Post by Bachstelze on 2010-08-23
> **KdotJ said:**
> Is this the preferred standard?

Yes.

[http://www.debian.org/doc/debian-policy/ch-files.html#s10.7.5](http://www.debian.org/doc/debian-policy/ch-files.html#s10.7.5)

---

### Post by KdotJ on 2010-08-23
> **Bachstelze said:**
> Yes.

[http://www.debian.org/doc/debian-policy/ch-files.html#s10.7.5](http://www.debian.org/doc/debian-policy/ch-files.html#s10.7.5)

Thanks for the link and making me wiser lol

---

### Post by hakermania on 2010-08-24
Thank you for your suggestion. Very useful...But what can you do if you don't want the user to be able to call your app globally in a terminal?
You have to put your app somewhere!
And this place is a bin dir usually...But if you put your app in a bin dir then everybody could call it from a terminal...
In a first view this cause no problems, but in a second it does!

---

### Post by Bachstelze on 2010-08-24
> **hakermania said:**
> Thank you for your suggestion. Very useful...But what can you do if you don't want the user to be able to call your app globally in a terminal?
You have to put your app somewhere!
And this place is a bin dir usually...But if you put your app in a bin dir then everybody could call it from a terminal...
In a first view this cause no problems, but in a second it does!

The purpose of a DEB is to install programs system-wide, that all users can use.  If the program is meant to be executed only by one user, it DOES NOT belong in a DEB package.

---

