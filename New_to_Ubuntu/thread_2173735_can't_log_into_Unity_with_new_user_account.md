---
title: "can't log into Unity with new user account"
date: 2013-09-11
forum: New to Ubuntu
---

### Post by Marchello_Lippi on 2013-09-11
Hi all, 

I can't log into Unity with new user account, but it works fine in console. 
What can be wrong?

---

### Post by carl4926 on 2013-09-11
> **Marchello_Lippi said:**
> Hi all, 

I can't log into Unity with new user account, but it works fine in console. 
What can be wrong?
Graphics driver?

---

### Post by Marchello_Lippi on 2013-09-11
[COLOR=#DD4814][carl4926]("http://ubuntuforums.org/member.php?u=809261"),[/COLOR][COLOR=#000000] 

but it works fine for old user... 
So I don't think it is because of graphics driver. 
Other ideas? [/COLOR]

---

### Post by coffeecat on 2013-09-11
What happens when you try to log into the GUI with the new account? Do you see an error message?

---

### Post by Marchello_Lippi on 2013-09-11
[COLOR=#DD4814][COLOR=#990303][coffeecat]("http://ubuntuforums.org/member.php?u=129087"),[/COLOR][/COLOR]

nope, no error messages are displayed. 
It just freezes for a moment, then refreshes welcome screen.

---

### Post by carl4926 on 2013-09-11
What version of Ubuntu
Is your user that works using fallback?

---

### Post by Marchello_Lippi on 2013-09-11
[carl4926]("http://ubuntuforums.org/member.php?u=809261")[COLOR=#000000],[/COLOR][COLOR=#000000][I]


               ``What version of Ubuntu``[/I]
[/COLOR]
My Ubuntu version is 12.0.4 LTS

[COLOR=#000000][I]

                ``Is your user that works using fallback?``[/I]

[/COLOR]I shall answer if you will be so kind to describe what is fallback.

---

### Post by carl4926 on 2013-09-11
Unity 2D
Looks like old Ubuntu

---

### Post by Marchello_Lippi on 2013-09-11
> **carl4926 said:**
> Unity 2D
Looks like old Ubuntu


What does it mean to me? Should I upgrade current Ubuntu version for new user to start working in Unity? 

BTW, I used following command to create new user: 

[COLOR=#000000][FONT=Ubuntu Beta]sudo adduser user2[/FONT][/COLOR]

---

### Post by carl4926 on 2013-09-11
> **Marchello_Lippi said:**
> What does it mean to me? Should I upgrade current Ubuntu version for new user to start working in Unity? 



I was trying to establish if you were using the Unity Desktop or had employed the fallback mode for graphics reasons?
From your normal user - let us see

```
lspci -nnk
```

If you machine is up to date, all users benefit from those.

---

### Post by Marchello_Lippi on 2013-09-11
Ok, I'll check it at home in the evening. Thanks.

---

### Post by Jonathan Precise on 2013-09-12
> **Marchello_Lippi said:**
> Hi all, 

I can't log into Unity with new user account, but it works fine in console. 
What can be wrong?

Try:

```
chmod 744 *name-of-user*
```

That should fix it.

---

### Post by whitesmith on 2013-09-12
> **Marchello_Lippi said:**
> Hi all, 

I can't log into Unity with new user account, but it works fine in console. 
What can be wrong?

Do you own everything in /home? If not, that could explain your problem. To find out, open a terminal and type
```
ls -la ~
```Or, if the terminal opens in home (usual behavior) omit the ~ at the end. If you don't own everything, use **chmod** (run it as su) to change owner/group to you.

---

