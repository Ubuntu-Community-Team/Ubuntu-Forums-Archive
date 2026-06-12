---
title: "logging in"
date: 2007-11-30
forum: Philippine Team
---

### Post by dareymon on 2007-11-30
help. 

kung minsan po eh hindi nadedetect ng pc yung keyboard ko kaya lagi akong nag rerestart until ma detect na nya yung keyboard ko. pano po kaya ang gagawin ko d2?

---

### Post by loell on 2007-11-30
ano po ang ubuntu version ang ginagamit ninyo?

---

### Post by wilvyrux on 2007-11-30
bka yung keyboard u na ang may problem..try u magpalit or mag try ng ibang keyboard....

what distro yung gamit bro?

---

### Post by dareymon on 2007-11-30
ubuntu na 7.10 po yung gamit ko. na try ko na pong mag palit ng keyboard pero minsan po ah hindi nya ma detect parin yung keyboard ko.

---

### Post by loell on 2007-11-30
kung nasa windows po kayo, wala naman po bang problemang kagaya n'ito?


try nyo po ito, baka may magandang resulta

pag na detect na keyboard nyo at nasa desktop na kayo,

type nyo po sa terminal


```
sudo gedit /etc/gdm/gdm.conf
```


sa gedit , search nyo yung line ,

```
 FailsafeXServer=/etc/gdm/failsafeXServer
```

e-comment out nyo po katulad n'ito,

```
 #FailsafeXServer=/etc/gdm/failsafeXServer
```

then press save then exit. test nyo po kung ok na or ganoon pa rin.

---

### Post by dareymon on 2007-12-01
i tried to look po pero phrase not found daw po.

---

### Post by dareymon on 2007-12-01
soory po. nakita ko na po yung line na pinapahanap nyo. na comment out ko na po like you said pero uhm, hindi na nya po ma detect yung keyboard ko kahit restart ako ng restart. kaya hindi po ako mkapasok sa ubuntu ngayon.

---

### Post by dareymon on 2007-12-01
ayan. nakapasok na po ako ulit sa ubuntu. pero parang chambahan nalang po ata ang nangyayari kung ma dedetect ba or not tong keyboard ko. try ko po yung suggestion nyo to change my login window. pero ask ko lang po kung tatanggalin ko na po ba yung pag kaka comment kanina?

---

### Post by dareymon on 2007-12-01
na try ko na pong mag palit ng login window pero still kung minsan po eh hindi pa na dedetect yung keyboard ko.

---

### Post by loell on 2007-12-01
sige po ibalik nyo na lang  sa dati.

---

### Post by dareymon on 2007-12-01
thank you po sa mga suggestions. sana po matulungan nyo ko bout my prob :)

---

### Post by raxso on 2007-12-01
Ano pong keyboard mo usb ba o ps2

---

### Post by xtrm_redbull on 2007-12-01
Nakapag install na ko ng ubuntu sa 1 desktop pc na HP Pavillion at 2 laptop na Acer with European keyboards pero wala naman ako na encounter na ganitong problema kaylangan mo lang mgpalit ng keyboard layout, kahit sa mga locally built computers (not branded) eh gumagana nman lahat sila, kahit wireless keyboards.

Check mo yung keyboard mo for damage wires or maybe your using an M$ keyboard or some branded keyboard that requires a driver.

---

### Post by dareymon on 2007-12-01
ps2 po

---

### Post by mitchi on 2007-12-01
baka naman ung ps2 sa board mo ang may sira?

---

### Post by Pedro0727 on 2007-12-02
Oo tama sya, Baka nga sira n ung PS/2 port. try to use the USB keyboard

---

