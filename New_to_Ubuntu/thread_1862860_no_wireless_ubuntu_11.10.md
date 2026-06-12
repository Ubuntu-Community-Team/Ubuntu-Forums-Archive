---
title: "no wireless ubuntu 11.10"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by Kickinthedoor on 2011-10-17
Last night i updated to 11.10 and the wireless wont turn on. Installed the broadcom driver and still got no connection. When u drop down the options it says its turned off with the wireless switch. I tired hitting f2 and fn+f2 and it wont turn on. The switch  and wireless was work working before update. I have a dell inspiron 1545 and the box says the card is 802.11b/g mini card 1379 if that helps at all. Please help a noob out!

---

### Post by westie457 on 2011-10-17
Hi can you post the output of these terminal commands please.

```
lspci -vnn
```
```
lshw -C network
```
```
rflill list all
```

To open a terminal press Ctrl+Alt+T. To post the output, highlight in terminal then click New Reply back here and click the # at the top of the message pane, paste between the 2 [code] tags.

---

### Post by 23dornot23d on 2011-10-17
Check the link below .....

Others have run into the same problem there may be a solution ..... check for [COLOR=Red]**SOLVED**[/COLOR]

---

### Post by Kickinthedoor on 2011-10-17
> **westie457 said:**
> Hi can you post the output of these terminal commands please.

```
lspci -vnn
```
```
lshw -C network
```
```
rflill list all
```

To open a terminal press Ctrl+Alt+T. To post the output, highlight in terminal then click New Reply back here and click the # at the top of the message pane, paste between the 2 [code] tags.

Im currently at work with no wired conection. Im postong via my phone. And dont have my cradle cable to transfer the text. Is there somthing specific u want to see? Maybe i can just vopy if iy isnt all the info

---

### Post by Kickinthedoor on 2011-10-17
Sweeeet! I found the solution from the link 23dornot23d posted and got it goin.  there was a hard block on. [Rfkill unblock all] did the trick. Thanks to both of you for taking the time to help me!

---

### Post by mörgæs on 2011-10-17
Good, then please mark the thread 'solved'.

---

