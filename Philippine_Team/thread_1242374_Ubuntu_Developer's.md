---
title: "Ubuntu Developer's"
date: 2009-08-17
forum: Philippine Team
---

### Post by 54n050|u710n5 on 2009-08-17
Hello sa lahat ng mga software/electonic/web developer....
 
 
Ask ko lang if anung magandang Programming IDE in ubuntu tsaka ung well tested backend to run enterprise systems sa ubuntu.
 
Currently gamit ko na IDE is Netbeans and Mono Develop.
MySQL for RDBMS.

---

### Post by loell on 2009-08-17
"Enterprise Systems" is a vague term.

if you're programming in Java then ( Netbeans and Eclipse ) are more than enough choices.

if you're into C# /mono , then you're out of luck, because currently you only have monodevelop.

as for dynamic languages, any basic editor will just do.

---

### Post by Script Warlock on 2009-08-17
OT: hehehe, hirap naman basahin handle mo wala ba mas simple?

---

### Post by 54n050|u710n5 on 2009-08-17
Currently running na ung ERP system na ginawa ko sa isang client ko dito sa koronadal, ang server namin sa ngaun tsaka client na OS is M$. pero now nag propose ako na mag change nang platform.For RDBMS sa experience nu anu ang mas ok and well tested sa 2Oracle or MySQL?

---

### Post by loell on 2009-08-17
both can handle the load,  it only  comes down to whichever is easier to set up  for you.

---

### Post by frustphil on 2009-08-17
> **loell said:**
> "Enterprise Systems" is a vague term.

if you're programming in Java then ( Netbeans and Eclipse ) are more than enough choices.

if you're into C# /mono , then you're out of luck, because currently you only have monodevelop.

as for dynamic languages, any basic editor will just do.

Theoretically, I think it's easier to develop C#/mono apps in Linux as evidenced by GNOME-DO, Evolution, Banshee, F-spot, Cubano, etc. Help is readily available in almost all Linux forums. In fact I'm now learning C#. As for Java(based on my experience), I couldn't even install JDBC though I had no trouble making database-less app.:) But don't get me wrong, I'm no software developer so your experience could be different than mine...

---

### Post by .::welemski::. on 2009-08-17
rule of the thumb:

kung saan ka cofortable stick to it...

---

### Post by 54n050|u710n5 on 2009-08-18
Thanks for quick reply guys... I guess I'll stick to netbeans(java) since monodev is under improvement and development..
 
[]

---

### Post by daxumaming on 2009-08-18
I also use Netbeans, though not exclusively. Depending on my needs and mood at the time, you can see me also coding on Geany, Gedit, and even Emacs and Vim.
MySQL can handle your RDBMS needs, just make sure your design will not cause you headaches in the future. I've learned the hard way that too normalized tables will get you into performance trouble in the future albeit a smaller disk space. Make sure you also don't scrimp on RAM, 4GB should be the minimum (again, based on my experience).

I work for an electric cooperative, and MySQL has been managing our data (around 5M rows on 32 tables and still counting) without any problems. Oh, and do away with the GUI, keyboard, mouse, and monitor... something this important should be tucked away from prying eyes and secured by lock and key.

---

