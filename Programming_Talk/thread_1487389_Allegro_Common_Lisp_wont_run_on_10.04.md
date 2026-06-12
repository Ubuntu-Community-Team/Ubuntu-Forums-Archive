---
title: "Allegro Common Lisp wont run on 10.04"
date: 2010-05-18
forum: Programming Talk
---

### Post by digitalneoplasm on 2010-05-18
Hi, 

I am hoping you might be able to help me with an issue I am having as I have exhausted my other options. 

I have installed Allegro CL 8.2 from this site: [http://www.franz.com/downloads/clp/download](http://www.franz.com/downloads/clp/download) on Ubuntu 10.04 x64. 

When I try to run the "alisp" executable I receive the following message: 

dan@Jadzia:/usr/local/acl82express$ ./alisp
bash: ./alisp: No such file or directory

Naturally, the file is there:

dan@Jadzia:/usr/local/acl82express$ ls
acache         alisp.dxl            bin             develenv.cl  files.bu              index.htm        locales     splash.bmp    update.cl
acli8218.tpll  allegro-express      cg-obsolete.cl  devel.lic    franz.bmp             jil              misc        src           update.sh
aclissl.so     allegro-express.dxl  cgtree.cl       doc          gtk                   jlinker          opengl      tutorial.bmp  welcome.bmp
aclssl.so      allegro-express.pll  cgtree.txt      eli          gui-builder-tutorial  libacli8218t.so  orblink     update        xeli
alisp          ansicl               code            examples     hosts.cl              license.txt      readme.txt  update2.cl

I have checked the permissions and the files have the execute bit set and such. 

I have run this software without issue on Ubuntu 9.10 both x86 and x64, but something seems to be different about 10.04 which is breaking it. 

Thanks for your help!

Take care,

-Dan

---

### Post by digitalneoplasm on 2010-05-19
Ah, this is fixed with todays glib update. 

-Dan

---

