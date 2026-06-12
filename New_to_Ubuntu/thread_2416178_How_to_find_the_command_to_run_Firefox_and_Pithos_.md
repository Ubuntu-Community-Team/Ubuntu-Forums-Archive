---
title: "How to find the command to run Firefox and Pithos at startup?"
date: 2019-04-06
forum: New to Ubuntu
---

### Post by billy3xs on 2019-04-06
Thank you for looking!

It looks like I've entered Firefox and Pithos in the Startup GUI. But they don't start.
I tried copying a screenshot of the GUI but got errors trying to post.
 
I found the commands thru the Browse, but I don't actually know what I'm looking at!

/etc/firefox
/usr/bin/pithos

I tried just entering Firefox, one tutorial said that was all that's needed.
Your help and time is very appreciated!  
;)

---

### Post by SeijiSensei on 2019-04-06
The firefox executable is /usr/bin/firefox. I don't think /etc/firefox exists on Ubuntu systems. What version of Ubuntu are you running?

---

### Post by Rubi1200 on 2019-04-06
How did you enter the commands?

With the path or just the name of the application?

For example, to make Firefox run after login you only need to enter firefox when adding to the Startup GUI.

---

### Post by billy3xs on 2019-04-06
Thank you,
Ubuntu Ubuntu 18.0402 LTS
Intel® Core™ i5-3210M CPU @ 2.50GHz × 4 
Intel® Ivybridge Mobile
64-bit
I tried just Firefox before and it didn't work.
then I browsed and Cut&Pasted 

I'll try
/usr/bin/firefox
but the Pithos command is like this
/usr/bin/pithos

---

### Post by billy3xs on 2019-04-06
Holy Mackerel! it worked now they both work with,

/usr/bin/firefox

/usr/bin/pithos
thank you so much!    :popcorn::)

---

### Post by Rubi1200 on 2019-04-06
Glad you got this resolved :-)

---

### Post by oldos2er on 2019-04-06
> **billy3xs said:**
> Holy Mackerel! it worked now they both work with,

/usr/bin/firefox

/usr/bin/pithos
thank you so much!    :popcorn::)

You could also do something like ```
apropos web browser
``` for firefox.

---

