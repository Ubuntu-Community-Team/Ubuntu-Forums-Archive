---
title: "Python poplib recent mail check"
date: 2008-05-16
forum: Programming Talk
---

### Post by kaivalagi on 2008-05-16
Hi All,

I am writing a little script to check mail (both IMAP and POP). I have it sort of working for both protocols, thanks to the easy to use poplib and imaplib libraries, but need some advice on getting a count of "recent" pop messages...

I think I can do this with IMAP with the RECENT flag in a .search() call, but how do I go about it for POP? I am currently getting the full count of messages which is far from ideal. Getting a recent (unread still on server) message count must be possible as there are other tools out there which do this.

My little function:
```
    def getPOPEmailCount(self,servername,ssl,username,password):
        if ssl == True:
            pop = poplib.POP3_SSL(servername)
        else:
            pop = poplib.POP3(servername)            
        
        pop.user(username)
        pop.pass_(password)
        count, size = pop.stat() #get first in sequence - message count
        pop.quit()
        
        return str(count)
```

Any pointers? Any help very much appreciated!

---

### Post by days_of_ruin on 2008-05-16
I have tried making email checkers and have tried to use one from a
python book but they never work for me.:confused:

---

