---
title: "HOWTO: Evolution with tray icon and new mail pop-ups"
date: 2006-10-17
forum: Outdated Tutorials &amp; Tips
---

### Post by simplyw00x on 2006-10-17
Email is definitely more productive when it's used less like traditional mail - checked once or twice a day, and dealt with in batches - and more like a forum/IM system. The problem with evolution is that, even though it can remain open, it takes up a fair amount of space on the window list, and doesn't notify you of new mail. this decreases productivity significantly, so we need a work-around.

**[SIZE="5"]Evolution pop-up notifications:[/SIZE]**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=17731&stc=1&d=1161103375[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=17730&stc=1&d=1161103304[/IMG]
To get these freaky-awesome libnotify pop-ups (kudos to [http://iapart.net/tresc.php?id=17&jezyk=2](http://iapart.net/tresc.php?id=17&jezyk=2)) , we need to re-compile evolution. But don't worry, this is a fairly painless process.

Before we start, ensure you have necessary basic packages:
```
sudo aptitude install build-essential fakeroot debhelper dh-make libnotify-dev
```

First, we need to download the evolution source, and install all the build dependencies:
```
cd
apt-get source evolution
sudo apt-get build-dep evolution
```

Now, we need to download and apply the evolution-libnotify patch:
```
wget http://iapart.net/evo/mail-ops.patch
cd evolution*/mail/
patch -p0<../../mail-ops.patch
cd ../
rm ../mail-ops.patch
```

Now all we have to do is make the package:
```
dpkg-buildpackage -rfakeroot -us -uc
```


Wait for it to finish (may take a while) then:
sudo dpkg -i ../evolution*.deb

Now you're done: make sure that your accounts are set to auto-check your mail, and you'll get notifications whenever you have new mail.

[SIZE="5"]**Tray icon evo with Alltray**[/SIZE]
Install alltray:
```
sudo aptitude install alltray
```
then create a launcher with the command:
```
alltray -na --key "F12" evolution --component=mail
```

Now you can click an icon or press F12 to get your evolution inbox at any time, and it will still send notifications as described above when minimised to tray.

---

### Post by deadlydeathcone on 2006-10-20
Thanks, this is great! The only caveat is that it displays the notifications in the lower-left corner of the screen, not the upper-right like you'd expect.

I made an Edgy Eft deb with pbuilder if anyone wants to try it.

[evolution_libnotify.tar.bz2]("http://www.uploading.com/files/HDRHY0Y2/evolution_libnotify.tar.bz2.html")

---

### Post by stalefries on 2006-10-20
Thank you so much! I was wondering how to do this!

---

### Post by Anonii on 2006-10-21
There is no dpkg-buildpkg command.
So, try this, in the step where you create the .deb package.

**sudo dpkg-buildpackage -rfakeroot -us -uc**

---

### Post by bodhi.zazen on 2006-10-31
Nice How-to simplyw00x

This thread has been added to the UDSF wiki.

[HOWTO: Evolution with tray icon and new mail pop-ups](http://doc.gwos.org/index.php/Evolution_Tray_icon_Mail_pop-ups)

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by as33 on 2006-10-31
Please publish the patch. iapart.net is down :(

---

### Post by drfindley on 2006-11-01
Through some google-cache trickery I was able to get the patch.  It's included in my attachement.  Just move it from mail-ops.patch.txt to mail-ops.patch

---

### Post by as33 on 2006-11-02
> **drfindley said:**
> Through some google-cache trickery I was able to get the patch.  It's included in my attachement.  Just move it from mail-ops.patch.txt to mail-ops.patch

show must go on :)

```
mail-ops.c:56:10: error: #include expects "FILENAME" or <FILENAME>
mail-ops.c: In function 'fetch_mail_fetch':
mail-ops.c:282: error: 'NotifyUrgency' undeclared (first use in this function)
mail-ops.c:282: error: (Each undeclared identifier is reported only once
mail-ops.c:282: error: for each function it appears in.)
mail-ops.c:282: error: expected ';' before 'urgency'
mail-ops.c:283: error: 'NOTIFY_EXPIRES_DEFAULT' undeclared (first use in this function)
mail-ops.c:284: error: 'NotifyNotification' undeclared (first use in this function)
mail-ops.c:284: error: 'notify' undeclared (first use in this function)
mail-ops.c:333: warning: implicit declaration of function 'notify_init'
mail-ops.c:354: warning: implicit declaration of function 'notify_notification_new'
mail-ops.c:359: warning: implicit declaration of function 'notify_notification_set_urgency'
mail-ops.c:359: error: 'urgency' undeclared (first use in this function)
mail-ops.c:360: warning: implicit declaration of function 'notify_notification_set_timeout'
mail-ops.c:362: warning: implicit declaration of function 'notify_notification_show'
mail-ops.c: In function 'mail_get_messagex':
mail-ops.c:1881: warning: assignment from incompatible pointer type
mail-ops.c: In function 'save_messages_save':
mail-ops.c:2034: warning: unused variable 'fd'
make[5]: *** [mail-ops.lo] Error 1
```

---

### Post by HaxTbh on 2006-11-03
Sorry ignore this

---

### Post by simplyw00x on 2006-11-03
> show must go on 
You need to have the libnotify-dev library installed:
```
sudo aptitude install libnotify-dev
```

---

### Post by harty83 on 2006-11-03
Two things:

One: I followed this tutorial to the "T" but am not getting notifications.  Am I missing something?

Two: Any clue how to keep update notifier from constantly wanting to update evolution after the patch is applied?

I've tried to lock the version but it is not working.

---

### Post by kelbizzle on 2006-11-04
Does this work in Edgy with Evolution v.2.8.1??

---

### Post by simplyw00x on 2006-11-04
> One: I followed this tutorial to the "T" but am not getting notifications. Am I missing something?
make sure that ```
ps -e | grep notification
```
outputs something, preferably along the lines of:
```
 9665 ?        00:00:00 notification-da
```

> Two: Any clue how to keep update notifier from constantly wanting to update evolution after the patch is applied?
sudo aptitude hold evolution

---

### Post by harty83 on 2006-11-04
> make sure that
```
ps -e | grep notification
```

outputs something, preferably along the lines of:
```
9665 ? 00:00:00 notification-da
```


This is what I get:

```
alan@hartysdesktop:~/evolution-2.8.1$ ps -e | grep notification
 6843 ?        00:00:42 notification-da
```

Is that good or bad?  What do I do now?

kelbizzle 
> Does this work in Edgy with Evolution v.2.8.1??

I am using Edgy but am not getting it to work.

---

### Post by simplyw00x on 2006-11-05
> Is that good or bad? What do I do now?
Try
sudo aptitude install libnotify-bin

then
notify-send Foo Foo

If that works, then it's a problem with evolutuin. If not, it's a problem with libnotify.

---

### Post by harty83 on 2006-11-05
I installed libnotify-bin and did your test and it worked.  But now when I try to send a new message through Evolution or reply to a message it crashes.  I ran evolution from the command prompt and this is the error it gives:

```
** (evolution-2.8:9067): DEBUG: mailto URL command: evolution --component=mail %s
** (evolution-2.8:9067): DEBUG: mailto URL program: evolution
evolution: symbol lookup error: /usr/lib/evolution/2.8/components/libevolution-mail.so: undefined symbol: ineIntelset_spacing

```

Any clues?

---

### Post by harty83 on 2006-11-05
I reinstalled and I no longer get the error.  

But I do not get the notifications either.  So it must be something with evolution.  I applied the patch and compiled it using this set of instructions.  Any clue what went wrong?

Thanks!
Alan

---

### Post by as33 on 2006-11-07
> **simplyw00x said:**
> You need to have the libnotify-dev library installed:
```
sudo aptitude install libnotify-dev
```

```
as@bogdan:~$ apt-cache policy libnotify-dev 
libnotify-dev:
  Installed: 0.4.2-0ubuntu3
  Candidate: 0.4.2-0ubuntu3
  Version table:
 *** 0.4.2-0ubuntu3 0
        500 http://ru.archive.ubuntu.com edgy/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by harty83 on 2006-11-07
> **as33 said:**
> ```
as@bogdan:~$ apt-cache policy libnotify-dev 
libnotify-dev:
  Installed: 0.4.2-0ubuntu3
  Candidate: 0.4.2-0ubuntu3
  Version table:
 *** 0.4.2-0ubuntu3 0
        500 http://ru.archive.ubuntu.com edgy/main Packages
        100 /var/lib/dpkg/status

```

I have libnotify-dev installed and had it installed before I compiled evolution with the patch.

---

### Post by srf21c on 2006-11-15
Great write-up.  Btw, I'm curious what the advantages of this method are over just installing the mail-notification-evolution package from the edgy repos.

---

### Post by joerx on 2006-11-20
hey, great tutorial, works fine on my dapper with evo 2.6.1 :) 

the only thing is that i now get update noifcations for evo 2.6.1, but i guess i should do anything but install that update, as it would overwrite the now patched version of evo. am i right? :-k 

any idea how to suppress that update notification, without disabling the whole update notification thing?

---

### Post by mattman on 2006-11-20
I,m trying to apply this patch on Evo 2.8.1 in Edgy and I keep running into this error> patching file mail-ops.c
Hunk #1 succeeded at 55 with fuzz 2 (offset 3 lines).
Hunk #2 succeeded at 512 with fuzz 2 (offset 239 lines).
Hunk #3 FAILED at 567.
1 out of 3 hunks FAILED -- saving rejects to file mail-ops.c.rej

this is whats in the mail-ops.c.rej file > ***************
*** 557,562 ****
                                        g_ptr_array_set_size (uids, cache_uids->len);
                                        for (i = 0; i < cache_uids->len; i++)
                                                uids->pdata[i] = g_strdup (cache_uids->pdata[i]);
                                        camel_uid_cache_free_uids (cache_uids);

                                        fm->cache = cache;
--- 567,610 ----
                                        g_ptr_array_set_size (uids, cache_uids->len);
                                        for (i = 0; i < cache_uids->len; i++)
                                                uids->pdata[i] = g_strdup (cache_uids->pdata[i]);
+
+                                       if (!notify_init("notify-send")){
+                                                       fprintf(stderr,"notify init nie powiodlo sie !");
+                                       }
+                                       else {
+
+                                         for(i=0; i< uids->len; i++)
+                                         {
+                                               message = camel_folder_get_message(folder, uids->pdata[i], &mm->ex);
+
+                                               if (message->reply_to)
+                                                       address = message->reply_to;
+                                               else if (message->from)
+                                                       address = message->from;
+                                               else continue;
+                                               if (!camel_internet_address_get (address, 0, &name, &str))
+                                                                       continue;
+                                               NotifyNaglowek = g_malloc(strlen(name)+strlen(str)+10);
+                                               snprintf(NotifyNaglowek,strlen(name)+strlen(str)+10,"From: %s",(name)?name:str);
+                                               NotifyBody = g_malloc(strlen(message->subject)+10);
+                                               snprintf(NotifyBody,strlen(message->subject)+10,"Subject: %s",message->subject);
+
+                                               notify  = notify_notification_new(NotifyNaglowek,
+                                                                               NotifyBody,
+                                                                               "/usr/share/icons/gnome/48x48/stock/net/stock_mail-open.png",
+                                                                               NULL);
+                                               if(notify==NULL) fprintf(stderr,"notify = NULL !!\n");
+                                               notify_notification_set_urgency(notify, urgency);
+                                               notify_notification_set_timeout(notify, expire_timeout);
+
+                                               notify_notification_show(notify, NULL);
+
+                                         }
+                                        // if(notify!=NULL)
+                                       //        g_object_unref(G_OBJECT(notify));
+                                       }
+
+
                                        camel_uid_cache_free_uids (cache_uids);

                                        fm->cache = cache;



---

### Post by falkenberg_cph on 2006-11-21
this doesnt seem to work anylonger.
Am i right?

First of i get an error when typing:
apt-get source evolution - it says it cannot find the source.

Secondly, if i move on and ignore this message - since i know i have evolution installed - this part also creates problem:

> 
wget [http://iapart.net/evo/mail-ops.patch](http://iapart.net/evo/mail-ops.patch)
cd evolution*/mail/
patch -p0<../../mail-ops.patch
cd ../
rm ../mail-ops.patch 


Its says it cant find the folder.

Well, can anyone tell me if they can make it work, or perhaps make an update of the how to.

Oh. i use Edgy and Evolution 2.8.1
and im very new to linux

Thanks
Carsten

---

### Post by deadlydeathcone on 2006-11-21
I'll post new packages with fixed version numbers when I (hopefully) get a new computer in a few days, as there's no way the one I have now could make it through a compile.

As far as the patch is concerned: is there a way to attach the notification to an arbitrary GTK widget, or would alltray have to be patched to allow such a thing?

edit:

> **falkenberg_cph said:**
> this doesnt seem to work anylonger.
Am i right?

First of i get an error when typing:
apt-get source evolution - it says it cannot find the source.

Make sure you have all of your source repositories enabled in Synaptic. Go to System -> Administration -> Software Sources and make sure the "source code" button is checked, then sudo apt-get update. Everything *should* work from there.

---

### Post by hrabeX on 2006-12-13
during making package I have this problem:
```

dh_shlibdeps -pevolution  -l :debian/evolution/usr/lib/evolution/2.8  
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnss3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsmime3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libssl3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsoftokn3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnss3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsmime3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libssl3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsoftokn3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnss3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsmime3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libssl3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsoftokn3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnss3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsmime3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libssl3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsoftokn3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnss3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsmime3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libssl3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsoftokn3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnss3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsmime3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libssl3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsoftokn3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnss3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsmime3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libssl3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsoftokn3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnss3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsmime3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libssl3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsoftokn3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnss3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsmime3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libssl3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsoftokn3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnss3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsmime3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libssl3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsoftokn3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnss3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsmime3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libssl3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libsoftokn3.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplds4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libplc4.so' not recognized
dpkg-shlibdeps: warning: format of `NEEDED libnspr4.so' not recognized


```

---

### Post by victorbrca on 2007-02-07
Also having problems here... Followed the instructions precisely, however I got some error msgs after  ## dpkg-buildpackage -rfakeroot -us -uc ##.

My .deb file also did not get created.

```
mail-ops.c:56:10: error: #include expects "FILENAME" or <FILENAME>
mail-ops.c: In function 'fetch_mail_fetch':
mail-ops.c:282: error: 'NotifyUrgency' undeclared (first use in this function)
mail-ops.c:282: error: (Each undeclared identifier is reported only once
mail-ops.c:282: error: for each function it appears in.)
mail-ops.c:282: error: expected ';' before 'urgency'
mail-ops.c:283: error: 'NOTIFY_EXPIRES_DEFAULT' undeclared (first use in this function)
mail-ops.c:284: error: 'NotifyNotification' undeclared (first use in this function)
mail-ops.c:284: error: 'notify' undeclared (first use in this function)
mail-ops.c:333: warning: implicit declaration of function 'notify_init'
mail-ops.c:354: warning: implicit declaration of function 'notify_notification_new'
mail-ops.c:359: warning: implicit declaration of function 'notify_notification_set_urgency'
mail-ops.c:359: error: 'urgency' undeclared (first use in this function)
mail-ops.c:360: warning: implicit declaration of function 'notify_notification_set_timeout'
mail-ops.c:362: warning: implicit declaration of function 'notify_notification_show'
mail-ops.c: In function 'mail_get_messagex':
mail-ops.c:1881: warning: assignment from incompatible pointer type
mail-ops.c: In function 'save_messages_save':
mail-ops.c:2034: warning: unused variable 'fd'
make[5]: *** [mail-ops.lo] Error 1
make[5]: Leaving directory `/home/victor/evolution-2.8.1/mail'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/victor/evolution-2.8.1/mail'
make[3]: *** [all] Error 2
rm GNOME_Evolution_Mail.server.in
make[3]: Leaving directory `/home/victor/evolution-2.8.1/mail'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/victor/evolution-2.8.1'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/victor/evolution-2.8.1'
make: *** [debian/stamp-makefile-build] Error 2
```


```
victor@victor-laptop:~/evolution-2.8.1$ sudo dpkg -i ../evolution*.deb
Password:
dpkg: error processing ../evolution*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ../evolution*.deb
```


```
victor@victor-laptop:~$ apt-cache policy libnotify-dev 
libnotify-dev:
  Installed: 0.4.2-0ubuntu3
  Candidate: 0.4.2-0ubuntu3
  Version table:
 *** 0.4.2-0ubuntu3 0
        500 http://ca.archive.ubuntu.com edgy/main Packages
        100 /var/lib/dpkg/status
```


BTW, can I delete these?

```
victor@victor-laptop:~$ ls -l
drwxr-xr-x 22 victor victor     4096 2007-02-07 20:43 evolution-2.8.1
-rw-r--r--  1 victor victor   363000 2007-02-07 20:42 evolution_2.8.1-0ubuntu4.diff.gz
-rw-r--r--  1 victor victor     1132 2007-02-07 20:42 evolution_2.8.1-0ubuntu4.dsc
-rw-r--r--  1 victor victor 17782443 2006-10-02 18:04 evolution_2.8.1.orig.tar.gz
```

Thanks,


Vic.

---

### Post by simplyw00x on 2007-02-08
Victor, make sure you have the corrent libnotify-dev packages installed.

---

### Post by me4oslav on 2008-08-20
For me works perfectly.Thanks.Great howto!

---

### Post by jdorenbush on 2008-09-29
It installed fine, but... it is buggy. Mine went to the tray the first time I opened Evolution, but now I don't have the tray icon anymore.

---

### Post by prometheus16 on 2008-12-07
Yeah, thanks for this.  I've been looking for a way to get this functionality.

---

### Post by Cuco3 on 2010-01-01
Is this tutorial still valid today? I need a tray icon for Evolution that checks for new email even if Evolution is not running.

---

### Post by Aragwain on 2010-04-27
This you can do with cGmail tool or something like that. Maybe GMail Notifier. You just install, configure and it checks for new mail every (for example, by me) 1 minute.

---

