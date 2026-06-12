---
title: "Error encountered while Installing Postfix"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by chandrasekhar3 on 2014-07-28
Hi everyone,

              I have faced one issue when i am trying to install the command like this

sudo apt-get install postfix mailutils libsasl2-2 ca-certificates libsasl2-modules

Processed some point of view and installed almost all at the end of Get:26 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe mailutils amd64 1:2.99.98-1.1 [225 kB]
Fetched 13.4 MB in 7min 47s (28.7 kB/s)                                        
Preconfiguring packages ...
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)

    The above given detailed text of error display please check it out as soon as possible!!! 

 Thanks & Regards,
A.Chandrasekhar

---

### Post by ubudog on 2014-07-28
Can you post the output of:
```
ls -al /usr/bin/dpkg
```

---

### Post by chandrasekhar3 on 2014-07-28
ls: cannot access /usr/bin/dpkg: No such file or directory

I can't find this directory as it was deleted somewhere, how can i get back that directoy, please give me solution, 

Thank YOU

---

### Post by ubudog on 2014-07-28
From [this]("http://ubuntuforums.org/showthread.php?t=1856256&page=2&p=11325182#post11325182") post, this may help you.

**32-bit system:**
```
mkdir /tmp/dpkg
cd /tmp/dpkg
wget http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4_i386.deb
ar x dpkg*.deb data.tar.gz
tar xfvz data.tar.gz ./usr/bin/dpkg
sudo cp ./usr/bin/dpkg /usr/bin/
sudo apt-get update
sudo apt-get install --reinstall dpkg
```

**64-bit system:**
```
mkdir /tmp/dpkg
cd /tmp/dpkg
wget http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4_amd64.deb
ar x dpkg*.deb data.tar.gz
tar xfvz data.tar.gz ./usr/bin/dpkg
sudo cp ./usr/bin/dpkg /usr/bin/
sudo apt-get update
sudo apt-get install --reinstall dpkg
```

This is a relatively old dpkg release, but I think you should be able to ugprade it with the last command.

---

### Post by chandrasekhar3 on 2014-07-29
Hi everyone,

       I am trying to install Postfix onto the machine but it is not trying to fix it, please suggest some options.



     $ sudo /etc/init.d/postfix reload
    * Reloading Postfix  configuration...  
      postfix/postfix-script: fatal: the Postfix mail system is not running                                                                                                                                postfix/postfix-script: fatal: the Postfix mail system is not running

  Thank you

---

### Post by chandrasekhar3 on 2014-07-29
hi,

    Thanks for the solution, You have done a fabulous job, once again thank u very much, may i know your name.

---

### Post by chandrasekhar3 on 2014-07-29
Hi I have one more doubt regarding after the config of postfix id has been done correctly, but i am unable to send an email to any mailid through command-line, what will be the issue here? can you notice this issue and give any suggestion for me?

sudo /etc/init.d/postfix reload
 * Reloading Postfix configuration...                                    [ OK ]

echo "Test mail from postfix" | mail -s "Test Postfix" <e-mail address>, this cmd is not sending mail to specific mailid, thanks.

---

### Post by mörgæs on 2014-07-29
Threads merged. Please don't multipost.

---

### Post by chandrasekhar3 on 2014-07-29
Hi everyone,

          Hi, I am getting the output of pstfix status in the below mentioned,
    
          sudo service postfix status
        * postfix is not running

       While goving postfix check it is not showning any result,
  
Thank You.

---

### Post by lisati on 2014-07-29
***Threads merged***
Please post the output of the following:
```
sudo service postfix start
```

---

