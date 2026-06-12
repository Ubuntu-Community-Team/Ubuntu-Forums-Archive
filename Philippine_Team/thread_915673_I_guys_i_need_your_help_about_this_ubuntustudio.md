---
title: "I guys i need your help? about this ubuntustudio"
date: 2008-09-10
forum: Philippine Team
---

### Post by kyme on 2008-09-10
Guys when i open my Synaptic Package Management an error appeared;

  >  
   W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
  
  
  how will i solve this? bago lang kasi ako sa ubuntu, wla masyado
  knowledge pag configure sa mga errors.
 PLease help me ..

---

### Post by loell on 2008-09-10
may nag reply na sa isa mong thread na kaparehas nito,

anyway, to solve your problem, you'll have add a key ,just copy paste this in terminal and hopefully the error will go away.

```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

---

