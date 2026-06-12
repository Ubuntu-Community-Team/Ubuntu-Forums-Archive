---
title: "Need some assitance for Evolution and accessing folders in dual boot"
date: 2009-05-14
forum: Philippine Team
---

### Post by randytan on 2009-05-14
Hi All!

I encountered a problem with Evolution recently when they changed a few settings in the office network. I could receive email but could not send out. I wound up installing Thunderbird and had to change the SMTP port number before I could send email. Is there a way to change the SMTP port number in Evolution so that I can use it again?

In the event that there is no work around for this, I will most likely use Thunderbird with Lightning to take over Evolution. I got one thing I want to change though, is there a way to reflect the 24Hr time format in Lightning and Thunderbird? Also, is there a way to import the email from Evolution to Thunderbird?

A friend of mine is still dual booting due to some applications that are needed in the office which we haven't figured out how to run in WINE yet. He is asking if it's possible to or if there is a way for him to access his Home folder while he is using xp?

Thanks.

Hope to hear from y'all again soon.

Best regards! :D

---

### Post by dgoosens on 2009-05-14
> 
In the event that there is no work around for this, I will most likely use Thunderbird with Lightning to take over Evolution. I got one thing I want to change though, is there a way to reflect the 24Hr time format in Lightning and Thunderbird?


I had this same problem... and the solutions I found online did not work on Ubuntu 9.04.

I created a thunderbird.sh file with this in it:
```

 #!/bin/sh
export LC_TIME=en_DK.utf8
mozilla-thunderbird

```

just put this file somewhere and change the properties of your shortcuts...
this did the trick on my end...

---

### Post by loell on 2009-05-14
> **randytan said:**
> 
A friend of mine is still dual booting due to some applications that are needed in the office which we haven't figured out how to run in WINE yet. He is asking if it's possible to or if there is a way for him to access his Home folder while he is using xp?

he can use [http://ext2fsd.sourceforge.net/]("http://ext2fsd.sourceforge.net/") driver to access the partition once installed you'll see it as normal folder/HD in windows file expplorer.

---

### Post by randytan on 2009-05-15
> **dgoosens said:**
> I had this same problem... and the solutions I found online did not work on Ubuntu 9.04.

I created a thunderbird.sh file with this in it:
```

 #!/bin/sh
export LC_TIME=en_DK.utf8
mozilla-thunderbird

```

just put this file somewhere and change the properties of your shortcuts...
this did the trick on my end...

Hi dgoosens,

How exactly do I go about doing this? I'm still kind of a newbie when it comes to doing coding stuff. :oops:

Can you give me a step by step instruction?

Thanks. :)

---

### Post by dgoosens on 2009-05-15
well, in first instance, you should make the file...

thus, on your desktop, create a file called "thunderbird" and put the code in it:
```

 #!/bin/sh
export LC_TIME=en_DK.utf8
mozilla-thunderbird

```

then, the easiest way is to use this file to launch Thunderbird.
to do this, you have to make it executable
this is the easiest in the termnial
```

$ chmod +x ~/Desktop/thunderbird

```

now you have to replace the existing link in your /usr/bin/ with this file

First we back up your file

```

$ sudo mv /usr/bin/thunderbird /usr/bin/thunderbird.BU

```

and finally we move the file you created on your Desktop into the /usr/bin directory

```

sudo mv /home/dgoosens/Desktop/thunderbird /usr/bin/thunderbird

```

there... you're done...
all the shortcuts you had should now launch Thunderbird correctly

hope it helps...

dgoosens

---

### Post by randytan on 2009-05-16
Hi dgoosens,

So I type all those out on the terminal?

How do I go about saving the script you posted on the desktop?

Once I have done what you said, can the script on the desktop be moved?

Thanks.

Hope to hear from you again soon. :)

---

### Post by dgoosens on 2009-05-18
Hi,

you have to type them all in the terminal except the first one...

for this file, you have to create a text file
right-click on your desktop > create document > Empty file 
and call it thunderbird.

When you will be done with all of it, there will no longer be any file on your Desktop as it will have been moved to /usr/bin

---

### Post by randytan on 2009-05-18
Thanks dgoosens.

Will try this once the workload lightens a bit. :D

---

