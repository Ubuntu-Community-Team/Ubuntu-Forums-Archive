---
title: "Need a programing volunteer for a small script"
date: 2011-05-28
forum: Programming Talk
---

### Post by gandaran on 2011-05-28
hi,
I don't know anything about programing so can you help with a script to send SMS using voipbuster? it should be easy I think, read the attachment, I use that code in a web browser but would prefer using a gui instead where I only fill in the message and hit the send button, even a nautilus script will do.
thanks in advance.

---

### Post by Petrolea on 2011-05-28
Here you go :)
Code is pretty straightforward so you can fix it easily if something's wrong.

```

addr="https://www.voipbuster.com/myaccount/sendsms.php?username="
usr=`zenity --entry`
pass=`zenity --entry`
from=`zenity --entry`
to=`zenity --entry`
text=`zenity --entry`
echo "$addr$usr&password=$pass&from=$from&to=$to&text=$text"

```

Save it as something.sh then chmod it with
```
chmod 777 something.sh
```

and then execute it:
```
./something.sh
```

You will be prompted to type the required stuff and it will make an output like this:

```
https://www.voipbuster.com/myaccount/sendsms.php?username=usr&password=pass&from=from&to=to&text=text
```

---

### Post by ziekfiguur on 2011-05-28
I couldn't really test it, because I don't use voipbuster myself. But, I think this should work.

---

### Post by gandaran on 2011-05-28
> **ziekfiguur said:**
> I couldn't really test it, because I don't use voipbuster myself. But, I think this should work.
thanks, it really works well:), but cant it be made to store the username, password and my phone number so that I only have to enter the destination phone and text?
thanks again for your time.

---

### Post by gandaran on 2011-05-28
> **Petrolea said:**
> Here you go :)
Code is pretty straightforward so you can fix it easily if something's wrong.

```

addr="https://www.voipbuster.com/myaccount/sendsms.php?username="
usr=`zenity --entry`
pass=`zenity --entry`
from=`zenity --entry`
to=`zenity --entry`
text=`zenity --entry`
echo "$addr$usr&password=$pass&from=$from&to=$to&text=$text"

```

Save it as something.sh then chmod it with
```
chmod 777 something.sh
```

and then execute it:
```
./something.sh
```

You will be prompted to type the required stuff and it will make an output like this:

```
https://www.voipbuster.com/myaccount/sendsms.php?username=usr&password=pass&from=from&to=to&text=text
```
thank you
I'm not sure what I have to type in the text field so I haven't tried your script, I prefer the way ziekfiguur's script works and will use it.
any way thank you for your time.

---

### Post by ziekfiguur on 2011-05-29
> **gandaran said:**
> thanks, it really works well:), but cant it be made to store the username, password and my phone number so that I only have to enter the destination phone and text?
thanks again for your time.

The username and phone number can be stored without a problem. However for the password I can't think of a way to store it securely without having to type another password to unlock it. I can store it in plaintext, but then everyone with access to your computer would be able to read it.

I'll do it for the username and phone number this evening, as i don't have a lot of time today. Please tell me if you want your password (unsafely) stored as well.

---

### Post by gandaran on 2011-05-29
> **ziekfiguur said:**
> The username and phone number can be stored without a problem. However for the password I can't think of a way to store it securely without having to type another password to unlock it. I can store it in plaintext, but then everyone with access to your computer would be able to read it.

I'll do it for the username and phone number this evening, as i don't have a lot of time today. Please tell me if you want your password (unsafely) stored as well.  
okay, keep the password as it is, its no big deal typing it every-time.
thanks again.

---

### Post by Petrolea on 2011-05-29
> **gandaran said:**
> thank you
I'm not sure what I have to type in the text field so I haven't tried your script, I prefer the way ziekfiguur's script works and will use it.
any way thank you for your time.

You can see in script what you need to type. First 'zenity' window requires username, second pass and so on, it is written in code (the zenity part).

If you want your username and password or something else to be fixed, just change `zenity --entry...` part to "your text". 

```

addr="https://www.voipbuster.com/myaccount/sendsms.php?username="
usr="change this to user name"
pass="your password"
from=`zenity --entry --text="From:"`
to=`zenity --entry --text="To:"`
text=`zenity --entry --text="Text:"`
echo "$addr$usr&password=$pass&from=$from&to=$to&text=$text"

```

I added text this time also.

---

### Post by ziekfiguur on 2011-05-29
Now it should remember the name and phone number after you send a message for the first time.

---

### Post by gandaran on 2011-05-29
> **ziekfiguur said:**
> Now it should remember the name and phone number after you send a message for the first time.
ziekfiguur

wonderful! thank you so much.

---

