---
title: "[SOLVED] evolution mail, broken Pipe"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Dutch70 on 2008-06-14
Hello, 

 I am trying to send an email and I keep getting this message.

"Error while performing operation."
"Could not send message: Broken pipe"

What can I do about that?  


"off topic" 
 does anyone know a good way to email screenshots, I believe I done that earlier today, but I kinda stumbled across it I guess, cause I cant find how to do it now.

---

### Post by iaculallad on 2008-06-14
Try installing exim4:

```
sudo apt-get install exim4
```

---

### Post by Dutch70 on 2008-06-14
Wow, it worked! this stuff never ceases to amaze me. I have no idea what that done, but it worked...:)

Thanks, I,ve been trying to figure that out...whew!..seems like forever.

---

### Post by iaculallad on 2008-06-14
> **Dutch70 said:**
> Wow, it worked! this stuff never ceases to amaze me. I have no idea what that done, but it worked...:)

Thanks, I,ve been trying to figure that out...whew!..seems like forever.

That was an MTA issue: "Broken Pipe"

---

