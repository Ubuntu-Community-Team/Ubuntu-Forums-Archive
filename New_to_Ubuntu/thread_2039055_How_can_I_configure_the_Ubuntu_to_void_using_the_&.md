---
title: "How can I configure the Ubuntu to void using the &quot;sudo&quot; to flash my Nandfalsh device"
date: 2012-08-08
forum: New to Ubuntu
---

### Post by sy373466062 on 2012-08-08
I'm flasing the nandflash which has mounted to PC, and I want to operate the NandFlash mounted as sdc , according the directions by given papers, I should do following:
   
  ```
  $ sudo ./flash sdc image
```

  How can I configure to void using the sudo to run this command so this Server PC  can be  safe be uesd by others.

 PS: 
       My English is poor and this is the first time for me to post the English thread , naturely, my posts may be not clear, it will be grateful for U to indicate my English mistakes, thanks for helping advance.:)

---

### Post by sy373466062 on 2012-08-13
> **sy373466062 said:**
> I'm flasing the nandflash which has mounted to PC, and I want to operate the NandFlash mounted as sdc , according the directions by given papers, I should do following:
   
  ```
  $ sudo ./flash sdc image
```

  How can I configure to void using the sudo to run this command so this Server PC  can be  safe be uesd by others.

 PS: 
       My English is poor and this is the first time for me to post the English thread , naturely, my posts may be not clear, it will be grateful for U to indicate my English mistakes, thanks for helping advance.:)


It is sad that no one helps me...

---

### Post by uRock on 2012-08-13
Hello and welcome to the forums,

If accounts do not have Administrative privileges, then they can't use sudo.

If you are looking to change the executable's permissions so that you can run it without sudo, then **cd** to the location and run **sudo chmod +x name**.```
sudo chmod +x name
```

Please do not be passive agressive in getting a response. Simply bumping the thread once every 24 hours will get attention to a thread.

---

### Post by Wim Sturkenboom on 2012-08-14
> **uRock said:**
> 
Please do not be passive agressive in getting a response.Please don't forget OP is not native English speaking. So it might be unintentional (or maybe not).

---

