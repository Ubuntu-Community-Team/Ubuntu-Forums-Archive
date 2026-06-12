---
title: "Python reading configfiles help wanted."
date: 2018-05-08
forum: Programming Talk
---

### Post by tomasvdmeer1989 on 2018-05-08
Hellow all =)

I'm reaching the borders of bash files, so i started programming with python. This spring i purchased a simple pc, for keeping files safe, just a backup plan.
I know i have to use minidom for this. but a little help i will appreciate. I've taken a look on different boards, and i have still a few questions.

the xml code i want to parse is:```

<afin>  
    <installautomation>
        <aptitudechain>vlc firefox nano leafpad</aptitudechain>
    </installautomation>
    <filesync user="username1">
        <sync serverpath="/3tbdisk/docs clientpath="/3tbdisk/docs" interval="60s" manual="true">Documents directory</sync>
        <sync serverpath="/3tbdisk/software clientpath="/3tbdisk/software" interval="60m" manual="true">Software directory</sync>
        <sync serverpath="/3tbdisk/$user/home/$USER clientpath="/home/$USER" interval="60m" manual="true">Users home directory</sync>
    </filesync>
    <filesync user="username2">
        <sync serverpath="/home/$USER/somedir clientpath="/home/$USER/somedir" interval="60m" manual="true">somedir</sync>
    </filesync>
</afin>  

```
Afin is the name of the project.
username1 & username2 are real usernames. So my script can check what user is logged on. Trust me it is needed, because i'm maintaining the whole thing.
What i mean with &USER: its just a automation of placement in the userdirectory.

The first question is, Did i setup this code correctly?
Is it able to do with minidom?
Is out there someone that can give me an example with echo of the <filesync> part, it is not needed, but i would really appreciate that, is doesn’t need to be exactly the code i need to copy.
Is is able to user $variables in the code, without using regular expressions?
is it able to use start tag like <filesync> with a variable in it? so, how?

Thx in advance.

---

### Post by tomasvdmeer1989 on 2018-05-14
I want to delete my acount.. how do i?

---

