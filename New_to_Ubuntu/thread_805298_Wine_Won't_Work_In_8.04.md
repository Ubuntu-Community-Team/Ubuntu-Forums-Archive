---
title: "Wine Won't Work In 8.04"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by carusoswi on 2008-05-23
I have Crossover Standard and also Wine.  Both were working in previous Ubuntu versions, neither will work now.  What is wrong and how should I fix it?
Thanks.

Caruso

---

### Post by logos34 on 2008-05-23
I feel your pain.  Same with me when I upgraded to Hardy.  I finally fixed it by rolling back from .60 to the wine version I was using in Gutsy (.47).  (archived [here]("http://wine.budgetdedicated.com/archive/index.html")).

On the other hand, release 1.0 rc1 now also works for me so I upgraded.

Or maybe try rc2 which I hear is just out (avail only at wine hq)

---

### Post by carusoswi on 2008-05-23
> **logos34 said:**
> I feel your pain.  Same with me when I upgraded to Hardy.  I finally fixed it by rolling back from .60 to the wine version I was using in Gutsy (.47).  (archived [here]("http://wine.budgetdedicated.com/archive/index.html")).

On the other hand, release 1.0 rc1 now also works for me so I upgraded.

Or maybe try rc2 which I hear is just out (avail only at wine hq)

Thanks for the reply.  Where do I find 1.0 rcl (and does it install the same as the version I downloaded from my applications menu?

Caruso

---

### Post by logos34 on 2008-05-23
> **carusoswi said:**
> Thanks for the reply.  Where do I find 1.0 rcl (and does it install the same as the version I downloaded from my applications menu?

I think it's the same, but not sure (and I notice it doesn't show the version number anywhere).

To be sure just do:

sudo synaptic

search wine

---

### Post by carusoswi on 2008-05-24
> **logos34 said:**
> I think it's the same, but not sure (and I notice it doesn't show the version number anywhere).

To be sure just do:

sudo synaptic

search wine

I do not see that version under my synaptic.  I went to the wine site and downloaded the WINE-1.0-RCL.TAR.BZ2 package, have extracted it to its own directory on my desktop, don't know what to do with it from there.  Don't see any instructions or "code steps" on the site.  Any suggestions?

Caruso

---

### Post by logos34 on 2008-05-24
> **carusoswi said:**
> I do not see that version under my synaptic.  I went to the wine site and downloaded the WINE-1.0-RCL.TAR.BZ2 package, have extracted it to its own directory on my desktop, don't know what to do with it from there.  Don't see any instructions or "code steps" on the site.  Any suggestions?

extract it and look inside the folder for a INSTALL or README.txt file.

Most likely all you have to do is open a terminal and run

cd wine-1.0-rc2

./configure

make 

sudo make install

(or [checkinstall]("https://help.ubuntu.com/community/CheckInstall") if you want to make a .deb)

---

### Post by BlackDragonBE on 2008-05-24
Thanks logos34, I always wondered how to make a deb file, now I know!

Cheers

---

### Post by tramir on 2008-05-24
You don't need to compile it, they provide a repo with the latest debs. You can find the instructions at [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb).

---

### Post by logos34 on 2008-05-24
> **tramir said:**
> You don't need to compile it, they provide a repo with the latest debs. You can find the instructions at [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb).

yes, but rc2 was just released--it's not avail yet in the repos (rc1)

---

### Post by carusoswi on 2008-05-24
> **logos34 said:**
> extract it and look inside the folder for a INSTALL or README.txt file.

Most likely all you have to do is open a terminal and run

cd wine-1.0-rc2

./configure

make 

sudo make install

(or [checkinstall]("https://help.ubuntu.com/community/CheckInstall") if you want to make a .deb)

What did I do wrong.  When I run make, I get a stop message ' no targets specified, no make file found.  
Caruso

---

### Post by carusoswi on 2008-05-24
> **carusoswi said:**
> What did I do wrong.  When I run make, I get a stop message ' no targets specified, no make file found.  
Caruso


Maybe this info will help you tell me what I'm doing wrong:

wine-1.0-rc2
caruso@caruso-desktop:~/Desktop/newwine$ ./configure
bash: ./configure: No such file or directory
caruso@caruso-desktop:~/Desktop/newwine$ cd wine-1.0-rc2
caruso@caruso-desktop:~/Desktop/newwine/wine-1.0-rc2$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

---

### Post by schtufbox on 2008-05-24
> **logos34 said:**
> yes, but rc2 was just released--it's not avail yet in the repos (rc1)
It is, it updated for me earlier.

---

### Post by jolx on 2008-05-24
> **carusoswi said:**
> Maybe this info will help you tell me what I'm doing wrong:

wine-1.0-rc2
caruso@caruso-desktop:~/Desktop/newwine$ ./configure
bash: ./configure: No such file or directory
caruso@caruso-desktop:~/Desktop/newwine$ cd wine-1.0-rc2
caruso@caruso-desktop:~/Desktop/newwine/wine-1.0-rc2$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

not sure whats wrong, have you installed build-essential?

it'd be way easier to just add the repo [here]("http://www.winehq.org/site/download-deb") like tramir suggested
it's already got rc2

---

### Post by HotShotDJ on 2008-05-24
Please don't try compiling this from source.  You are just begging for heartache.  Use the WineHQ repositories.  This will keep you up to date on Wine releases using TESTED packages especially created for Ubuntu Hardy.  Contrary to a previous post, 1.0_RC2 is there.

Follow the instructions here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
You will save yourself A LOT of problems.

---

### Post by logos34 on 2008-05-24
> **schtufbox said:**
> It is, it updated for me earlier.

Yep, you're right.  Turns out I had my pre-release updates (Hardy-proposed) unchecked in synaptic>repos.  (duh) Now it shows up.

As far as compiling from source (in my case following the x64 Wine HQ hardy instructions), I too ran into the same snag--no 'make' file (??).  Not sure what the deal is.  But since there's a .deb for rc2 [here too]("http://wine.budgetdedicated.com/archive/index.html"), no reason to compile after all

---

### Post by carusoswi on 2008-05-25
> **logos34 said:**
> Yep, you're right.  Turns out I had my pre-release updates (Hardy-proposed) unchecked in synaptic>repos.  (duh) Now it shows up.

As far as compiling from source (in my case following the x64 Wine HQ hardy instructions), I too ran into the same snag--no 'make' file (??).  Not sure what the deal is.  But since there's a .deb for rc2 [here too]("http://wine.budgetdedicated.com/archive/index.html"), no reason to compile after all

Well, I appreciate the help.  Would never have tried compiling from source except that it was suggested since rc2 was not in the repos when I first embarked on a solution.  In any event, if I follow directions, I should be able to compile, right, when everything is working.

Have since installed from the repos, but, the new version of wine did not solve my problems.  I cannot run MS Office from Ubuntu since upgrading to 8.04.  MS Access is the only MS AP I have to use on a daily basis, now, I'm stuck either going back to XP or downgrading back to Ubuntu 7.10.  Too bad.

Caruso

---

