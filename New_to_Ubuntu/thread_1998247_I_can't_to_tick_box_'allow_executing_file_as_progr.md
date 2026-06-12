---
title: "I can't to tick box 'allow executing file as program"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by Martin Bannister on 2012-06-05
> **drewster911 said:**
> Hello, I am having the same problem.  Trying to run "openarena.x86_64", used to have no issues running it, and other executables too.  I did a "chmod +x", then while in openarena folder "./openarena.x86_64", says permission denied.  try "sudo ./openarena.x86_64", says "command not found' wtf?
try to change permisssion on openarena.x86_64 by checking "allow executing", will not stay checked

these permission isssue confuse the crap out of me

I'm having the same problem, 'will not stay checked', when trying to run XMind from a USB stick!  

Can anyone help with that?  I've tried the terminal commands on the file too and that doesn't work.  

Thanks,
Martin.

---

### Post by tgm4883 on 2012-06-06
> **Martin Bannister said:**
> I'm having the same problem, 'will not stay checked', when trying to run XMind from a USB stick!  

Can anyone help with that?  I've tried the terminal commands on the file too and that doesn't work.  

Thanks,
Martin.

Your USB stick is probably formatted FAT or NTFS, which don't support Linux permissions.

Also if check the date of the thread before you post, this one is over a year old.

---

### Post by coffeecat on 2012-06-06
@Martin Bannister, I've moved your post and tgm4883's reply into its own thread in the Beginner's section where you are more likely to get help for your particular issue. It is better to start your own threads and as tgm4883 says, please check the date of previous posts before posting anywhere.

---

### Post by snowpine on 2012-06-06
Copy it to your /home folder and try again.

---

