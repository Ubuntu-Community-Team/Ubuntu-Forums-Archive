---
title: "save in termninal problem"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by 007casper on 2008-09-02
trying to set dns server... after you insert text to "named.conf.local"
"tm.local.db" in the terminal... how do you save it?

I tried "Ctrl + O" didnt work, then tried "Ctrl + X"... 

please advise thank you

---

### Post by lapubell on 2008-09-02
what commands are you using?

are you editing the config file with nano?  or setting the dns with the commands?

can you be a bit more descriptive?

---

### Post by 007casper on 2008-09-02
following the directions here...
[http://howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind-p4](http://howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind-p4)
-
I am not editing the config file with nano.  I am setting the dns with the commands in the terminal. Using "root" as a user...

I am new to ubuntu and dont know anything about nano... a bit frustrated because I have seen so many different posts that is oudated regarding setting up dns servers, and people having setting up issues.  I think the link above was the most recent without too many frustrated user comments.

In any case, it doesnt mention how to save the inserted text for files for...
"named.conf.local" ; "tm.local.db" ; "named.conf.options" 

thank you so much for your help

---

### Post by 007casper on 2008-09-02
I am using vi as my text editor. After I have inserted text, I have tried :w and it didnt work... then I tried ZZ no luck.

Please help

thank you

---

### Post by tacutu on 2008-09-02
in vi, first ESC (press escape), then :wq

---

### Post by 007casper on 2008-09-02
Awesome!  Thank you. Thank you so much :-)

One more thing when you type vi "/etc/network/interfaces" how do you go back to command prompt... tried esc... asked if I want to save or quit... tried to quit nothing happened then went to Terminal>reset... the command prompt came up but couldnt countinue

thank you so much

---

