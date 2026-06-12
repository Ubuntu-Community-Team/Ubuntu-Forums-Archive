---
title: "Using wget to download file from mega.nz"
date: 2016-01-25
forum: Programming Talk
---

### Post by erotavlas on 2016-01-25
Hi, I wonder to know if it is possible to download files from mega.nz cloud service by using wget. I tried without success with ```
 wget 'https://mega.nz/#!CV1gUDaS!cgcHDgsbMlENZlZ417qJq0aHTX8TEdrr8uhqqPkZ_No' 
``` but it downloads a strange index.html file. Thank you

---

### Post by howefield on 2016-01-25
Not sure you will get wget to work but megatools is a package in the repository that you can use to upload/download your files, although possibly only in the last cycle or two.

---

### Post by erotavlas on 2016-01-25
Ok, but it seems that there is not a stable package for ubuntu and I have to compile from source [https://github.com/megous/megatools](https://github.com/megous/megatools). Do you know about any package?

---

### Post by howefield on 2016-01-25
Wily has Megatools version 1.9.95 and xenial (current Ubuntu development version) has 1.9.96 - what version of Ubuntu are you using ?

---

### Post by erotavlas on 2016-01-25
I'm using ubuntu-lubuntu 14.04 and 12.04 and I'm writing a script. For this reason, I would like to use command line. Hence, I will wait for next release of Ubuntu.

---

### Post by erotavlas on 2016-02-01
Hi, I solved by making a script that downloads the source code of megatools and compiles it.  ```
megaToolsVersion="1.9.96" megaTools="/home/$USER/megatools-$megaToolsVersion" if [ ! -d $megaTools ]; then 	sudo apt-get -y install build-essential libglib2.0-dev libssl-dev libcurl4-openssl-dev libgirepository1.0-dev -y --force-yes --quiet 	cd /home/$USER 	wget "https://megatools.megous.com/builds/megatools-$megaToolsVersion.tar.gz" 	tar -xvf "./megatools-$megaToolsVersion.tar.gz" 	cd $megaTools 	./configure 	make 	cd .. 	rm -rf "./megatools-$megaToolsVersion.tar.gz" fi
``` After this I can use the tools via $megaTools/megadl

---

