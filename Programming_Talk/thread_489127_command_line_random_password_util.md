---
title: "command line random password util"
date: 2007-07-01
forum: Programming Talk
---

### Post by rubix64 on 2007-07-01
hey!

Im not sure if this is the correct forum for my post but here goes:

I have been using linux for about 6 months now and am starting to learn some bash scripting. I am working on a small hack that started because I decided that hands on was the best way to learn all this!

My objective is:

To write a script that will:

1-Make a secure connection to [https://grc.com/passwords.htm](https://grc.com/passwords.htm)
2-Grep the 3 random 64 character passkeys
3- output the 3 strings on 3 seperate lines on my terminal


thanks in advance for your help. I'm hoping that someone can take a second to help me learn.

cheers
Ruben

---

### Post by spin2cool on 2007-07-01
Off the top of my head:
1) getting the page is simple - just use 
'wget https://www.grc.com/passwords.htm'

2) then, you'll want to use some combination of grep and/or awk to match up the appropriate lines.  This will give you the four 63/64 character passwords, but won't include the two with the ASCII characters.  (Note that there are actually 6 passwords generated each time on that page)

'egrep -o "(\w{64}|\w{63})" passwords.htm'

---

### Post by rubix64 on 2007-07-01
wow, that did it!. Thanks so much, mate!

---

### Post by rubix64 on 2007-07-02
O.K.- so thanks to spin2cool's help I'm rolling on my project to create a script that will grep the ascii strings at grc.com.

Current code:

wget [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm)
egrep -o "(\w{64}|\w{63})" passwords.htm


Problems-

1) after egrep calls password.htm the file remains and repeating the script results in creating passwords.htm(2) etc. how to deleted passwords.htm after use--or is there a better way

2) is wget not as secure as https? If so is there a command line call that can duplicate the security of https ?

3) Do the keystrings pass through any unsecured areas of the system where they might be retained in memory and if so how do i address this?


PS- spin2cool-- could you please elaborate on why the page has 6 passwords. Im afraid my learning curve is a little steep this week!

Not to gush or anything but I'm really gooving on the open atmosphere here. I've received so much help from people that didn't have to spend their time helping someone they don't know but did and do

thanks,
Ruben

---

### Post by Modred on 2007-07-02
> **rubix64 said:**
> 1) after egrep calls password.htm the file remains and repeating the script results in creating passwords.htm(2) etc. how to deleted passwords.htm after use--or is there a better way
Add a command to remove the passwords.html file after you're done. (Note that **grep -E** should be the same as **egrep**.)
```
wget https://www.grc.com/passwords.htm
grep -E -o "\w{63,64}" passwords.htm
rm passwords.htm
```

> 2) is wget not as secure as https? If so is there a command line call that can duplicate the security of https ?
Https should be supported by wget and handled automatically.  I wouldn't be worried about this.

> PS- spin2cool-- could you please elaborate on why the page has 6 passwords. Im afraid my learning curve is a little steep this week!
Look further down the page.  When describing what each type of password is and its uses, a second password of that type is generated.  So 3 at the top and 3 in the descriptions.

---

### Post by Golyadkin on 2007-07-02
Well, there is also a program called mkpasswd that generates random password. Maybe that will be good for you too?

---

### Post by rubix64 on 2007-07-02
yes, mkpasswd is great! Thanks for recommending it. Really though it was more about finding a way to do that one task, even if other apps far surpass it in efficiency. I'm just trying to learn a little something about everything. Thanks to you all I have learned a little more.

I wonder how I might go about looking at the code of mkpasswd in order to see how it works. Is there a... repository of code somewhere <entry level question_cringe>

I don't program in c yet but Im currently trying to teach myself to do just that.

---

