---
title: "Can't import nmap in python3"
date: 2018-08-28
forum: New to Ubuntu
---

### Post by shenara on 2018-08-28
If I should post this elsewhere let me know. Basically, whenever I try to import nmap in python3 I get an error saying "ModuleNotFoundError: No module named 'nmap'". I think it may have something to do with the fact I created an alias for python2.7 (the ubuntu default I think?) to equal python3. I've tried running [sudo apt-get update && sudo apt-get install nmap] countless times to no avail. Any ideas? Thanks!

---

### Post by monkeybrain20122 on 2018-08-28
You should have done

```
sudo apt install python3-nmap
```

Also I don't know what you meant by

 > I created an alias for python2.7 (the ubuntu default I think?) to equal python3 

If you mean something like ```
alias python="/usr/bin/python3"
``` then it is a very bad idea because many system components rely on default python (2.7) and you will break things this way. You have to invoke python3 explicitly if you want to use it instead of python2

---

### Post by shenara on 2018-08-28
Thank you, friend! I did mean what you suggested, I'm just not yet good at articulating myself with computer related issues. That worked like a charm :)

---

