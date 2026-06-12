---
title: "Can't start synaptic anymore (error) and updates don't work anymore.."
date: 2008-08-26
forum: New to Ubuntu
---

### Post by kramer65 on 2008-08-26
Hello,

I recently tried to mess a bit around with adobe reader to get pdf's to work within firefox. Not only did I not succeed. I also messed a lot of things up. The update thing says there is an update for acroread, but that gives an error that says that there are broken packages. And when I try to open synaptic it says this: 

```
E: Type '<!DOCTYPE' op regel 1 in bronlijst /etc/apt/sources.list.d/medibuntu.list is onbekend
E: Kan de lijst van bronnen niet inlezen.
Ga naar de broninstellingen om het probleem te verhelpen.
E: _cache->open() failed, please report.
```

It has a lot of Dutch in it (I'm from the Netherlands), but it says that it can't read the list of sources and that I have to go to 'source-properties' to solve the problem.

Can anybody help out?

---

### Post by nicedude on 2008-08-26
So go to System -> Administration -> Software Sources and see if you can figure out what is wrong. I don't speak Dutch but it looks like a problem with yoru medibuntu repositories listings. You might try removing them and then adding them again per Medibuntu's guide at their site.

---

### Post by Elfy on 2008-08-26
Move the file and then install the medibuntu repos again - can't read dutch but it looks exactly the as in english. Run each command seperately - 

```
sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bak
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
I assume you are using hardy - if not change hardy

---

### Post by kramer65 on 2008-08-26
Hi forestpixie. I tried your commands. The first two ones go well. The last one gives some trouble. It downloads all this stuff and then says that 

the medibuntu-keyring is already the newest one, and that I probably want to do the 'apt-get -f install' to fix the following:
the following packages have not full demands/dependancies (something like it):
acroread-escript: demands: acroread but it will not be installed
  acroread-plugins: demands: acroread (= 8.1.2.su1-0.0medibuntu0.8.04.1) but it will not be installed
  mozilla-acroread: demands: acroread (= 8.1.2.su1-0.0medibuntu0.8.04.1) but it will not be installed
E: There are demands that are not done. You can best do 'apt-get -f install' without specifying packages, (or you can specify a solution yourself).

So I tried to do 'sudo apt-get -f install' which tells me that 3 packages where not fully installed or removed and that I can proceed which will download something of about 29mb and it will take about 74mb extra. type Y if you want to proceed. 
I type Y and then it doesn't download anything. It just says that acroread will be unpacked but that there is a mistake with /var/cache/apt/archives/acroread_8.1.2.su1-0.0medibuntu0.8.04.1_i386.deb (--unpack):
 trying overwriting `/usr/bin/acroread', which is also in package adobereader-enu 
Found mistakes while working on:
 /var/cache/apt/archives/acroread_8.1.2.su1-0.0medibuntu0.8.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

(Throughout the codes I translated some stuff, so it may not be standard thing it normally says..)

Does that help anything? What should I do now?

---

### Post by Elfy on 2008-08-26
Can you do - 
```
sudo apt-get install acroread
```

post the output as it is in Dutch please.

---

### Post by kramer65 on 2008-08-26
I did that and it gives me this:

```
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Statusinformatie wordt gelezen... Klaar
Aanbevolen pakketten:
  libxul0d
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  acroread
0 pakketten opgewaardeerd, 1 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
3 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 0B/29,5MB aan archieven opgehaald worden.
Na deze handeling, zal er 73,9MB extra schijfruimte gebruikt worden.
(Database inlezen ... 140304 bestanden en mappen geïnstalleerd.)
Uitpakken van acroread (uit .../acroread_8.1.2.su1-0.0medibuntu0.8.04.1_i386.deb) ...
dpkg: fout bij afhandelen van /var/cache/apt/archives/acroread_8.1.2.su1-0.0medibuntu0.8.04.1_i386.deb (--unpack):
 poging tot overschrijven van `/usr/bin/acroread', wat ook in pakket adobereader-enu zit
Fouten gevonden tijdens behandelen van:
 /var/cache/apt/archives/acroread_8.1.2.su1-0.0medibuntu0.8.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Elfy on 2008-08-26
Try to remove adobereader-enu and run apt-get install -f again

```
sudo apt-get remove adobereader-enu
sudo apt-get install -f
```

---

### Post by kramer65 on 2008-08-26
ok. The first one gave me this:

```
ricam@ricam-desktop:~$ sudo apt-get remove adobereader-enu
[sudo] password for ricam: 
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Statusinformatie wordt gelezen... Klaar
U wilt waarschijnlijk 'apt-get -f install' uitvoeren om volgende op te lossen:
De volgende pakketten hebben niet-voldane vereisten:
  acroread-escript: Vereisten: acroread maar het zal niet geïnstalleerd worden
  acroread-plugins: Vereisten: acroread (= 8.1.2.su1-0.0medibuntu0.8.04.1) maar het zal niet geïnstalleerd worden
  mozilla-acroread: Vereisten: acroread (= 8.1.2.su1-0.0medibuntu0.8.04.1) maar het zal niet geïnstalleerd worden
E: Er zijn niet-voldane vereisten. U kunt best 'apt-get -f install' uitvoeren zonder pakketten op te geven, (of u kunt zelf een oplossing specificeren).
```

and the second command gave me this:

```
ricam@ricam-desktop:~$ sudo apt-get install -f
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
Statusinformatie wordt gelezen... Klaar
Vereisten worden gecorrigeerd... Klaar
De volgende extra pakketten zullen geïnstalleerd worden:
  acroread
Aanbevolen pakketten:
  libxul0d
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  acroread
0 pakketten opgewaardeerd, 1 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
3 pakketten niet volledig geïnstalleerd of verwijderd.
Er moeten 0B/29,5MB aan archieven opgehaald worden.
Na deze handeling, zal er 73,9MB extra schijfruimte gebruikt worden.
Wilt u doorgaan [J/n]? j
(Database inlezen ... 140304 bestanden en mappen geïnstalleerd.)
Uitpakken van acroread (uit .../acroread_8.1.2.su1-0.0medibuntu0.8.04.1_i386.deb) ...
dpkg: fout bij afhandelen van /var/cache/apt/archives/acroread_8.1.2.su1-0.0medibuntu0.8.04.1_i386.deb (--unpack):
 poging tot overschrijven van `/usr/bin/acroread', wat ook in pakket adobereader-enu zit
Fouten gevonden tijdens behandelen van:
 /var/cache/apt/archives/acroread_8.1.2.su1-0.0medibuntu0.8.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Elfy on 2008-08-26
Ok - so it gives install -f again then

When you first installed acroread did it actually install properly, where you able ti use it.

Can you open synaptic? If you can, go to custom filters - and see if there are any broken.

You could try ```
sudo dpkg --reconfigure -a
```but I'm sure it will give install -f

---

