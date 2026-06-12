---
title: "Open Office Writer"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by ivann92 on 2008-09-01
Is the font Nimbus Roman on Open Office Writer the same as Times New Roman on Word.

---

### Post by jemate18 on 2008-09-01
> **ivann92 said:**
> Is the font Nimbus Roman on Open Office Writer the same as Times New Roman on Word.

Nimbus Roman No9 L is it? I think it is the closest thing to Times new roman

---

### Post by ivann92 on 2008-09-01
There is no such font as "Times".

---

### Post by jemate18 on 2008-09-01
You can also install microsoft fonts (including Times New Roman), type 
> sudo apt-get install msttcorefonts

---

### Post by jemate18 on 2008-09-01
> **ivann92 said:**
> There is no such font as "Times".

Sorry I was in Error check my above post to install times new roman

---

### Post by ivann92 on 2008-09-01
What do you mean install Times New Roman?

Never Mind, by install I am assuming you mean type that code in the terminal

---

### Post by jemate18 on 2008-09-01
> **ivann92 said:**
> What do you mean install Times New Roman?

Never Mind, by install I am assuming you mean type that code in the terminal

yes

When you type```
apt-get install msttcorefonts
```
it will install fonts including times new roman, because it is included in that package.. Did you try it?

---

### Post by ivann92 on 2008-09-01
Jemate, I did what you told me to do but for some reason i am unable to type my password.

---

### Post by jemate18 on 2008-09-01
> **ivann92 said:**
> Jemate, I did what you told me to do but for some reason i am unable to type my password.

So, nothing appears on the terminal when you are typing your password?

It is perfectly normal, after typing your password, press enter

---

### Post by CC_Joe on 2008-09-01
When you type in your password to the terminal, you don't see stars or anything else that lets you know you're typing. It's a security feature, that prevents anyone from seeing how many digits your password is.

If you just type your password normally and hit enter, it should work.

---

### Post by ivann92 on 2008-09-01
Now it is telling me that there is an error and it cannon access a certain locked file.

---

### Post by jemate18 on 2008-09-01
> **ivann92 said:**
> Now it is telling me that there is an error and it cannon access a certain locked file.

this error happens when your system is updating or when a package manager is currently upgrading.

Are you currently updating your system? if yes, wait for it to finish. if not, what is the exact error?

---

### Post by ivann92 on 2008-09-01
Ok, never mind I installed the fonts but now where can i find them?

---

### Post by jemate18 on 2008-09-01
> **ivann92 said:**
> Ok, never mind I installed the fonts but now where can i find them?

If you want to use them in openoffice, it is there on the formatting toolbar, the combobox of the fonts.

You can select it, it is available

---

### Post by jemate18 on 2008-09-01
OK check my attachment

---

### Post by ivann92 on 2008-09-01
I don't see it in the formatting toolbar, I still just see the same fonts as before.

---

### Post by ivann92 on 2008-09-01
I believe you but it is just not there for me.

---

### Post by jemate18 on 2008-09-01
> **ivann92 said:**
> I don't see it in the formatting toolbar, I still just see the same fonts as before.

Did the installation go smoothly?

To verify type
> dpkg --status msttcorefonts

Check for the status line. What does it says?

---

### Post by jemate18 on 2008-09-01
If the status is "install ok installed"

Try restarting your PC

---

### Post by ivann92 on 2008-09-01
For some reason when i verify it says that i have not installed the package and when i tried to install the package again it says that the package has been installed. It doesnt make sense.

---

### Post by jemate18 on 2008-09-01
> **ivann92 said:**
> For some reason when i verify it says that i have not installed the package and when i tried to install the package again it says that the package has been installed. It doesnt make sense.



Try restarting the PC..... Sometimes it makes wonders..

If this doesn't work... can you post the output of the command ```
dpkg --status msttcorefonts
```

---

### Post by ivann92 on 2008-09-01
It says the package is not installed and no information is available

---

### Post by jemate18 on 2008-09-01
> **ivann92 said:**
> It says the package is not installed and no information is available

Oh this is weird. You said you have executed
> sudo apt-get install msttcorefonts
And that it was successful

and after that you verified the file using 
> dpkg --status msttcorefonts
and it was installed

After restarting your PC executing
> dpkg --status msttcorefonts
says it was NOT installed.

This is strange....

can you execute this one more time.... Just to be able to verify
> sudo apt-get install msttcorefonts

---

### Post by ivann92 on 2008-09-01
When I type the enter the code it asks me if i want to install the extra packages; should I?

---

### Post by jemate18 on 2008-09-01
> **ivann92 said:**
> When I type the enter the code it asks me if i want to install the extra packages; should I?

yes..... and it should work after installation. You will be able to use it in openoffice writer......

---

### Post by ivann92 on 2008-09-01
No, even after that the new fonts aren't there.

---

### Post by jemate18 on 2008-09-01
> **ivann92 said:**
> No, even after that the new fonts aren't there.

Im sorry I wasn't able to solve your problem......... for one last time.... do you mind restarting your PC? sometimes that did the trick for some of my weird problems.....

---

### Post by ivann92 on 2008-09-01
Ok, will do. Thank you for all the help anyways.

---

