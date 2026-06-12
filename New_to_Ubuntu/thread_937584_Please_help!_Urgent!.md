---
title: "Please help! Urgent!"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by weece on 2008-10-04
Well my windows shat its self and I figured i'd install ubuntu after I got a cd sent to me just incase...

Okay so heres the problem.. i boot from the cd and go into try it out so when im at the desktop i click install... i get up to 50% partion and then the installer application closes down and I can't open it back up!!

Please help asap as my dad wants to reformat my computer with shitty windows!!
ps. step by step instruction for a noob (a)

---

### Post by Sef on 2008-10-04
1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Instead of booting or installing the Live CD go down to 'Check Disk for Errors'.

4) Run the Live CD for a while.   Report on any problems.

---

### Post by weece on 2008-10-04
I Got the cd sent to me (from the ubuntu website)so I dunno about that stuff.. I checked it for defaults and nothing is wrong.. 

ps thanks for your help


edit: ive been trying since last night.. I just can't get passed the partioning bit on the install

---

### Post by Sef on 2008-10-04
What are your system specs including the graphics card?

---

### Post by weece on 2008-10-04
i have an 80gb AMD Sempron desktop pc
Nidivia gForce graphics card and ummmm
i dunno how to check the other stuff

---

### Post by weece on 2008-10-04
ok i got to the who are you bit after the partioning bit and it froze.. so im restarting and trying again :(

---

### Post by Sef on 2008-10-04
I want to check the ram....so from the live cd > System > Administration > Terminal and type in this code:

```
free -m
```

copy and paste the results here.

---

### Post by weece on 2008-10-04
its 512mb ram

---

### Post by weece on 2008-10-04
still didnt work.. now what??

---

### Post by Sef on 2008-10-04
I'm wondering if your hard drive is bad...I'll have to find a way to check it, or someone else will have to.

---

### Post by weece on 2008-10-04
ok when i click instal/try ubuntu it comes up with this command screen and I cant get passed it.. what do i do

---

### Post by weece on 2008-10-04
can anyone at all help!?

---

### Post by Ryadt on 2008-10-04
> **weece said:**
> ok when i click instal/try ubuntu it comes up with this command screen and I cant get passed it.. what do i do

Try ```
startx
```

---

### Post by Lord DarkPat on 2008-10-04
I think it's either that your HDD is messed up or that the CD is bad. Even the Canonical ones can be faulty ;) (in fact any CD can be faulty)

---

