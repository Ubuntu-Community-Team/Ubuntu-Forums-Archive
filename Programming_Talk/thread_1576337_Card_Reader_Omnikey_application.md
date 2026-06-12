---
title: "Card Reader Omnikey application"
date: 2010-09-17
forum: Programming Talk
---

### Post by O-tek on 2010-09-17
Hi , 


I am programming an application to use a card reader (Omnikey 5321) but i have some several problems.

Details : Ubuntu 10.04 LTS ( full updated)
libs :  Omnikey Sync API, pcsc-tools 
language : C++
Reader : Omnikey 5321 contact and contactless card

My application find my reader can connect it and find if a smart card is inserted but : 
- I can't find the contactless interface 
- I can't communicate with my card.

Suggested solutions for communication with card: 
- Use ScardCLICCTransmit (function for card iClass (like mine)) but this function is undeclared :/

Herewith my "simplify" code, 

```


ScardEstablishContext(,,,,); <= Success
ScardGetStatusChange(,,,,); <=Success
ScardListReaders(,,,,); <= Success

ByteSend[] = {0xFF,0xCA,0x00,0x00,0x00}
ScardTransmit(,ByteSend,,&ByteRecv,) <=Success but return ByteRecv = 0x6e and 0x00; 
Normally this function should respond more than 2bytes. 


```

Thanks and sorry for my english ...

---

### Post by aybayrak on 2011-02-22
Hi O-tek 
Did you solve your problem ?

I am also working on an omnikey 5321usb. I installed pcsc-lite and Omnikey SYNC-API. But I cant get any feedback from card reader. I plug in  it to usb port but I dont get any change. I cant use Omnikey api. I could not open it:(. How can use this api Can you help ? 
Thank you & Best Regards

---

