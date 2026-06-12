---
title: "how do I enable desktop effects?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by bmann11 on 2008-06-24
When I go into System > Appearance > Visual Effects and then click on "normal" a message appears saying they aren't enabled.  Can anyone help with this?  Thanks.  By the way - using Hardy.

---

### Post by perlluver on 2008-06-24
> **bmann11 said:**
> When I go into System > Appearance > Visual Effects and then click on "normal" a message appears saying they aren't enabled.  Can anyone help with this?  Thanks.  By the way - using Hardy.

Do you have restricted drivers enabled?  Being your video card.

---

### Post by bmann11 on 2008-06-24
I don't know.  How do I ckeck that?

---

### Post by philinux on 2008-06-24
> **bmann11 said:**
> When I go into System > Appearance > Visual Effects and then click on "normal" a message appears saying they aren't enabled.  Can anyone help with this?  Thanks.  By the way - using Hardy.

Try 

System>Admin>Hardware Drivers.

What are you're full system specs.

---

### Post by niyonk on 2008-06-24
> **bmann11 said:**
> I don't know.  How do I ckeck that?

check above lol

---

### Post by perlluver on 2008-06-24
> **bmann11 said:**
> I don't know.  How do I ckeck that?

Go to system>administration>Restricted Drivers, I believe not in Ubuntu so I think that is where it is.

Edit:  To late, thanks to above for that info.

---

### Post by bmann11 on 2008-06-24
The only device listed when I follow the above directions is a 'software modem'.  So, I guess my answer to the question is, no I don't have my video card enabled.  

Thus, how do I enable it?

---

### Post by perlluver on 2008-06-24
What kind of video card do you have?  It might not be fast enough.

Edit: type lspci in the terminal, and give the output of that here.  That will help us know which video card you have.

---

### Post by bmann11 on 2008-06-24
Sorry for my display of utter newbness:) but how do I check what kind of video card I have?

---

### Post by jualin on 2008-06-24
To find out your video card type in the terminal > lspci and look for the VGA line. This will give us more information about your specific video card.

---

### Post by bmann11 on 2008-06-24
Here it is.

"01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)"

---

### Post by perlluver on 2008-06-24
[http://ubuntuforums.org/showthread.php?t=727371]("http://ubuntuforums.org/showthread.php?t=727371"), This thread might be of help to you.

---

### Post by jualin on 2008-06-24
maybe this thread will help you [http://http://ubuntuforums.org/showthread.php?t=727371]("http://http://ubuntuforums.org/showthread.php?t=727371")

*edit* This is funny how we answered with the same link.

---

### Post by bmann11 on 2008-06-24
Thanks, I'll root around through this for a bit.

---

### Post by Rocket2DMn on 2008-06-25
Your card doesn't use restricted drivers, so don't try to install them.  Have a look here for enabling Compiz - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

