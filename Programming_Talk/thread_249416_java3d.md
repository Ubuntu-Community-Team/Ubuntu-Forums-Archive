---
title: "java3d"
date: 2006-09-02
forum: Programming Talk
---

### Post by txutxu on 2006-09-02
guys how i install 


java3d-1_4_0_01-linux-amd64.bin 

i tried 

chmod +x java3d-1_4_0_01-linux-amd64.bin

./java3d-1_4_0_01-linux-amd64.bin

but dont work

i tried 

fakeroot make-jpkg /home/nilmesmo/Desktop/java3d-1_4_0_01-linux-amd64.bin
Creating temporary directory: /tmp/make-jpkg.XXXXskEFVt
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh
sh: gcc: comando não encontrado
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)



i have instaled JDK, JRE , java-package, build-essential

how install java 3D?

---

### Post by yaaarrrgg on 2006-09-02
FWIW, I just tried installing it on Dapper and never had any problems (well, I installed the i586 version for my CPU).

Perviously, I manually downloaded and installed  the 1.5 JDK from Sun, and build-essentials, so don't think you'd need anything other than that. 

All I did was:

sudo -i
chmod 755 thefile
./thefile

---

