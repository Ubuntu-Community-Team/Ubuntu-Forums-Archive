---
title: "Secure folder"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by imsudheer98 on 2012-08-21
I have been using Ubuntu 10.04 from a long time i have moved my desktop to secure state but now i am unable to change its status to normal can anyone help me with this?

---

### Post by sandyd on 2012-08-21
> **imsudheer98 said:**
> I have been using Ubuntu 10.04 from a long time i have moved my desktop to secure state but now i am unable to change its status to normal can anyone help me with this?
Hi, 

What do you mean by "secure state"?

Do you mean an encrypted home folder?

---

### Post by imsudheer98 on 2012-08-21
> **sandyd said:**
> Hi, 

What do you mean by "secure state"?

Do you mean an encrypted home folder?
I mean i moved my desktop folder into secure folder.

---

### Post by Bucky Ball on 2012-08-21
Don't quite follow. What is a secure folder? How did you secure it, exactly?

When you say 'secure state', do you mean it won't give you the permission to move or change the contents of the 'Desktop' folder now you have moved it out of /home and into another folder? What is the name of the 'secure' folder (full path if you could, please)? ;)

---

### Post by sandyd on 2012-08-21
I think the OP means an encrypted folder. (I.E. Not an encrypted home folder)

---

### Post by imsudheer98 on 2012-08-21
> **sandyd said:**
> I think the OP means an encrypted folder. (I.E. Not an encrypted home folder)

In home folder we have desktop and secure folders right? I have copied the desktop folder and pasted it in secure folder from that minute no one was able access my desktop except me.

---

### Post by imsudheer98 on 2012-08-21
> **Bucky Ball said:**
> Don't quite follow. What is a secure folder? How did you secure it, exactly?

When you say 'secure state', do you mean it won't give you the permission to move or change the contents of the 'Desktop' folder now you have moved it out of /home and into another folder? What is the name of the 'secure' folder (full path if you could, please)? ;)

I mean the secure folder we find in home folder. From the time when i moved the desktop folder into secure folder no one was able to access my desktop. I tried to move it out of it but no luck i am unable to move it back.

---

### Post by sandyd on 2012-08-21
Can you post a screenshot please? (Just press Print Screen on your keyboard to take a screenshot)

---

### Post by imsudheer98 on 2012-08-21
> **sandyd said:**
> Can you post a screenshot please? (Just press Print Screen on your keyboard to take a screenshot)

I have uploaded the screen shots first one is my home folder n the second is my desktop in secure folder i am unable to move desktop folder out of the secure folder.

I am a noob please bare with me..

---

### Post by Bucky Ball on 2012-08-21
Well, presuming you are using Nautilus, you could open it from a terminal with:
```

gksudo nautilus
```... then try copy your /secure/Desktop back to /home/user/Desktop, then delete /secure/Desktop. Don't do anything other than this. You could seriously screw your system as you'll have permission to do anything when Nautilus is launched as root like this.

But then, this could be an encryption issue as suggested by sandyd, a subject about which I know next to nothing ...

---

### Post by sandyd on 2012-08-21
> **imsudheer98 said:**
> I have uploaded the screen shots first one is my home folder n the second is my desktop in secure folder i am unable to move desktop folder out of the secure folder.

I am a noob please bare with me..
Open a terminal and run this
```

sudo mv ~/secure/Desktop ~/Desktop

```Whats your username btw?
You will need it in order to return the Desktop folder to normal after that.

The username is the section right before the "@" in your terminal.

For example, 
```

**username**@mycomputer:

```Once you know your username, 
run, replacing **username** with your real username
```

sudo chown -R **username**:**username** /home/**username**

```

---

### Post by imsudheer98 on 2012-08-21
> **Bucky Ball said:**
> Well, presuming you are using Nautilus, you could open it from a terminal with:
```

gksudo nautilus
```... then try copy your /secure/Desktop back to /home/user/Desktop, then delete /secure/Desktop. Don't do anything other than this. You could seriously screw your system as you'll have permission to do anything when Nautilus is launched as root like this.

But then, this could be an encryption issue as suggested by sandyd, a subject about which I know next to nothing ...

Actually i have done this to my system in my office so i cant do the thing what u said without admin password is there any way i can change it?

---

### Post by sandyd on 2012-08-21
you will have to wait for whoever your sysadmin is then.

---

