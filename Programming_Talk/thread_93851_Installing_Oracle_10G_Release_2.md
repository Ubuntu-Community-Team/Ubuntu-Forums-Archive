---
title: "Installing Oracle 10G Release 2"
date: 2005-11-22
forum: Programming Talk
---

### Post by nandipinto on 2005-11-22
Hi all,

I've been trying to install Oracle 10G Release 2 on my Ubuntu, I have followed all the instructions in this URL: 

[http://www.togaware.com/linux/survivor/Oracle_10g.shtml](http://www.togaware.com/linux/survivor/Oracle_10g.shtml)

However, I still got some errors during installation, and I chose to ignore the errors, though and installation was finished. The problem is, I couldnt even start the Oracle service and run the SQLPlus. I attached the log files with this post.

Could anyone, please help me?

Best regards,


nandipinto:confused:

---

### Post by daacon on 2005-11-26
I plan on installing Oracle 10g Release 1 this weekend. I tried to open the zip file you attcahed with Zip Genius can got invalid archive so I can read it. Post the errors in a reply and I'll see if I can help ya out. 

later..............dy

---

### Post by daacon on 2005-11-27
I was able to successfully Install Oralce 10g Release I - I still cannot read your zip file (I am Windoze here that maybe the issue) - if you cut and paste the error peiece out I can have a look later today perhaps. 

later..........dy

---

### Post by nandipinto on 2005-11-27
Hi there,

Glad to hear that, how did you do that? I got no luck with the installation, thou :( 
Btw, thanks for your reply, i'll try to attach the log files once again. I hope you could find some clues.


Best regards,


nandipinto

---

### Post by daacon on 2005-11-27
[http://ubuntuforums.org/showthread.php?t=16654&page=2&highlight=oralce+10g](http://ubuntuforums.org/showthread.php?t=16654&page=2&highlight=oralce+10g)

Basically followed someone elses instructions :-) - my last reply is on page 2

---

### Post by nandipinto on 2005-11-28
Hi all,

I'm wondering why I still get the same error during the installation, I chose to "Ignore" the errors - the installer says it was successfull, but when I tried to run SQLPlus for example, nothing happens :(
I have followed all the instructions, thou, what have I done wrong?

Rgds,


nandipinto.

---

### Post by daacon on 2005-11-29
Hi 

There is not enough information - Ignoring installtion errors is never a good thing and is the likley cause of a bad installation. Look at the installation log and see where the errors occured you can cut and paste them here. Or just attach the log file (it should not be that bigl). 

sqlplus 'not working' could be as complex as realted to the installation issue or as simple as a missing path statement. 

later..........dy

---

### Post by nandipinto on 2005-11-29
Hi daacon,

Forgot to mention that the errors occured when, I think, the installer is trying to compile some files with ".mk" extension - it's not in the log file, though.
 
Below are the content of ".err" file from the oraInventory/logs folder:

==================================================
java.lang.reflect.InvocationTargetException
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at oracle.sysman.oip.oipc.oipcr.OipcrRulesEngine.executeRule(OipcrRulesEngine.java:278)
        at oracle.sysman.oip.oipc.oipcp.OipcpPrereqChecker.executeCheck(OipcpPrereqChecker.java:495)
        at oracle.sysman.oip.oipc.oipcp.OipcpPrereqChecker.runChecks(OipcpPrereqChecker.java:450)
        at oracle.sysman.oip.oipc.oipcp.OipcpPrereqChecker.executePrereqs(OipcpPrereqChecker.java:351)
        at oracle.sysman.oii.oiif.oiifw.OiifwPrereqWCDE$1.run(OiifwPrereqWCDE.java:650)
        at java.lang.Thread.run(Unknown Source)
Caused by: java.lang.NullPointerException
        at oracle.sysman.oip.oipc.oipch.OipchLinuxVersion.getVersionParts(OipchLinuxVersion.java:533)
        at oracle.sysman.oip.oipc.oipch.OipchLinuxVersion.<init>(OipchLinuxVersion.java:77)
        at oracle.sysman.oip.oipc.oipch.OipchLinuxGlibcVersion.<init>(OipchLinuxGlibcVersion.java:19)
        at oracle.sysman.oip.oipc.oipch.OipchLinuxOSCreator.updateGlibcInfo(OipchLinuxOSCreator.java:207)
        at oracle.sysman.oip.oipc.oipch.OipchLinuxOSCreator.updateOSInfo(OipchLinuxOSCreator.java:136)
        at oracle.sysman.oip.oipc.oipch.OipchLinuxOSCreator.createOS(OipchLinuxOSCreator.java:120)
        at oracle.sysman.oip.oipc.oipch.OipchOSCreator.getOS(OipchOSCreator.java:106)
        at oracle.sysman.oip.oipc.oipch.OipchHostCreator.getOS(OipchHostCreator.java:84)
        at oracle.sysman.oip.oipc.oipch.OipchHostCreator.build(OipchHostCreator.java:57)
        at oracle.sysman.oip.oipc.oipck.OipckKnowledgeSourceFactory.getKnowledgeSourceImpl(OipckKnowledgeSourceFactory.java:239)
        at oracle.sysman.oip.oipc.oipck.OipckKnowledgeSourceFactory.getKnowledgeSource(OipckKnowledgeSourceFactory.java:60)
        at oracle.sysman.oip.oipc.oipck.OipckKnowledgeSourceLibrary.loadKnowledgeSource(OipckKnowledgeSourceLibrary.java:160)
        at oracle.sysman.oip.oipc.oipck.OipckKnowledgeSourceLibrary.getKnowledgeSource(OipckKnowledgeSourceLibrary.java:79)
        at oracle.sysman.oip.oipc.oipcr.OipcrRulesEngine.getKnowledgeSource(OipcrRulesEngine.java:563)
        at oracle.sysman.oip.oipc.oipcz.OipczOSChecks.checkCertifiedOSVersions(OipczOSChecks.java:69)
        ... 10 more


java.lang.UnsatisfiedLinkError: jniGetOracleHome
        at oracle.net.common.NetGetEnv.jniGetOracleHome(Native Method)
        at oracle.net.common.NetGetEnv.getOracleHome(Unknown Source)
        at oracle.net.ca.NetCA.main(Unknown Source)
Oracle Net Services configuration failed.  The exit code is -1


==============================================

I'm thinking of switching to Fedora/Redhat :(


rgds,


nandipinto

---

### Post by daacon on 2005-11-29
Well RedHat is a suported Oracle Platform as is SUSE. Fedora is a based on Red Hat and and Oracle install should be simpler. Simplier may not be the best term - more documented is a better description. You will still have to make system changes and likley have to install some pacakgages. 

I almost gave up and actually downloaded the 4 Fedora CD's but persisitance paid off and I now I have a working Oracle 10g database on Ubuntu :D 

Yes looks like you have linking errors - did you download all the packes listed in the docuemnt (make / and the others) ? Are you sure you have the required header files ( look in /usr/include/asm/ files like systen.h ) need to download the libc.dev or something like that. Have you run the root.sh scripts using sudo command ? 

Later............dy

---

### Post by nandipinto on 2005-11-30
Hi dacoon,

Thanks again for your reply, but still I got no luck with this. Below are the error messages during the installation, I got rpm error, eventhough I have installed the rpm package.
I really hope someone could show me the light :(

rpm: to install rpm packages on Debian systems, use alien.


1. Error in invoking target 'ntcontab.o' of makefile '/opt/oracle/product/10.2.0/db_1/network/lib/ins_net_client.mk'.

2. Error in invoking target 'nnfgt.o' of makefile '/opt/oracle/product/10.2.0/db_1/network/lib/ins_net_client.mk'.

3. Error in invoking target 'relink' of makefile '/opt/oracle/product/10.2.0/db_1/network/lib/ins_precomp.mk'.

4. Error in invoking target 'ioracle' of makefile '/opt/oracle/product/10.2.0/db_1/network/lib/ins_rdbms.mk'.

5. Error in invoking target 'client_sharedlib' of makefile '/opt/oracle/product/10.2.0/db_1/network/lib/ins_net_client.mk'.

6. Error in invoking target 'nnfgt.o mkldfagsclient_sharedlib' of makefile 'opt/oracle/prodct/10.2.0/db_1/network/lib/ins_net_client_mk'.

7. Error in invoking target 'install' of makefile 'opt/oracle/product/10.2.0/db_1/sqlplus/lib/ins_sqlplus.mk'

8. Error in invoking target 'irman' of makefile 'opt/oracle/product/10.2.0/db_1/rdbms/lib/ins_rdbms.mk'

9. Error in invoking target 'install' of makefile '/opt/oracle/product/10.2.0/db_1/network/lib/ins_net_client.mk'

10. Error in invoking target 'install' of makefile '/opt/oracle/product/10.2.0/db_1/plsql/lib/ins_plsql.mk'

11. Error in invoking target 'ntcontab.o nnfgt.o' of makefile '/opt/oracle/product/10.2.0/db_1/network/lib/ins_net_client.mk'

12. Error in invoking target 'ioklist iokinit iokdstry' of makefile '/opt/oracle/product/10.2.0/db_1/network/lib/ins_nau.mk'

13. Error in invoking target 'utilities ctx_on' of makefile '/opt/oracle/product/10.2.0/db_1/rdbms/lib/ins_rdbms.mk'

14. Error in invoking target 'install' of makefile '/opt/oracle/product/10.2.0/db_1/ctx/lib/ins_ctx.mk'

15. Error in invoking target 'agent nmo nmb' of makefile '/opt/oracle/product/10.2.0/db_1/sysman/lib/ins_sysman.mk'

16. Error in invoking target 'clientonlyinstall' of makefile '/opt/oracle/product/10.2.0/db_1/ldap/ins_ldap.mk'

17. Error in invoking target 'install' of makefile '/opt/oracle/product/10.2.0/db_1/srvm/lib/ins_srvm.mk'

18. Error in invoking target 'racg_install' of makefile '/opt/oracle/product/10.2.0/db_1/racg/lib/ins_has.mk'

19. Error in invoking target 'intall' of makefile '/opt/oracle/product/10.2.0/db_1/network/lib/ins_net_server.mk'

20. Error in invoking target 'all_no_orcl ihsodbc' of makefile '/opt/oracle/product/10.2.0/db_1/rdbms/lib/ins_rdbms.mk'

21. Error in invoking target 'collector' of makefile '/opt/oracle/product/10.2.0/db_1/sysman/lib/ins_emdb.mk'

22. File not found %fileName%


rgds,

nandipinto

---

### Post by daacon on 2005-12-01
Hello 

Sounds frustration for sure you are installing Release 2 (I installed release 1 ) but it should work. My guess for your latest attempt is the initial root.sh file you need to run during the installation was not successful 
 
-	Maybe start completely over –

Remove all oracle products  

sudo rm -fr '/opt/oracle/
as well the Installation Log directory

Make sure your environment variables are set (either in your .bashrc or set them explicitly)  before you run the installer

umask 0022
export ORACLE_BASE=/opt/oracle/ 
export ORACLE_HOME='/opt/oracle/product/10.2.0/db_1/’
export ORACLE_SID=<database-name>
export PATH=$PATH:$ORACLE_HOME/bin
export EMHOSTNAME=<machine-name>

The EMHOSTNAME is set for Enterprise Manager if you are setting up a starting db

When you run the Installer after a few minutes you will be prompted to run a script called root.sh - make sure you run this as root or if root is not enable as a user that has sudo privileges (the original user you set up)  The first script set some permissions and I don't think it prompts you. Once that runs successfully (make sure it does) go back to the installer. 

A little while later you will be prompted to run another script as root. This one will prompt for some variables. Again make sure this script runs successfully as a root user or with sudo. I have noticed if I run root.sh or any command as a non sudo user no errors appear so it looks like script executed successfully.

---

### Post by nandipinto on 2005-12-02
Hi Dacoon,

I've set all variables you told me and run the root.sh as root user. I've even re-installed Ubuntu and all required packages. 
I also tried to install 10gR1, but I guess I'm facing the same wall, have no idea what else I can do.
I'm installing on my Compaq Presario v2000, I hope this has nothing to do with the errors.


rgds,

nandipinto

---

### Post by daacon on 2005-12-04
Hi nandipinto

Well not sure. If Ubuntu installs ok I doubt is is anything to do with the Hardware.  Here is another guide ...(not english but easy enough to read)

[http://www.spazidigitali.com/media/Oracle_su_ubuntu.pdf](http://www.spazidigitali.com/media/Oracle_su_ubuntu.pdf)

May be time to choose which is more of a priority for you Unbuntu or Oracle (there are other databases for Unbuntu) Fedora is a free download and SUSE has a free distro as well I think - if your set on Oracle may be time to switch 

I also tried to install Oracle 10g IAS - could not even get past the installer yet - so for me looks like I can run an Oracle  database and that's it. I may switch myself  if I need more Oracle components. 

But I hate to give up on Ubuntu cause everthing else I have tried just works !!!! 

later..........dy

---

### Post by remohammadi on 2006-05-03
I have a problem in installation. in Linking 'Oracle Database 10g 10.2.0.1.0' step.
The message is :

[SIZE="1"]Exception Name: MakefileException
Exception String: Error in invoking target 'install' of makefile '/share/app/oracle/product10_1/ctx/lib/ins_ctx.mk'. See '/share/app/oracle/oraInventory/logs/installActions2006-05-03_09-01-16PM.log' for details.[/SIZE]

tail of '/share/app/oracle/product10_1/install/make.log' :

[SIZE="1"]gcc **-m32** -o **ctxhx** -L/share/app/oracle/product10_1/ctx//lib32/ -L/share/app/oracle/product10_1/lib32/ -L/share/app/oracle/product10_1/lib32/stubs/  /share/app/oracle/product10_1/ctx/lib/ctxhx.o -L/share/app/oracle/product10_1/ctx/lib/ -ldl -lm -lctxhx -Wl,-rpath,/share/app/oracle/product10_1/ctx/lib -lsnls10 -lnls10  -lcore10 -lsnls10 -lnls10 -lcore10 -lsnls10 -lnls10 -lxml10 -lcore10 -lunls10 -lsnls10 -lnls10 -lcore10 -lnls10  `cat /share/app/oracle/product10_1/lib/sysliblist`[/SIZE]

/usr/bin/ld: skipping incompatible /lib/libpthread.so.0 when searching for /lib/libpthread.so.0
/usr/bin/ld: cannot find /lib/libpthread.so.0
collect2: ld returned 1 exit status
make: *** [ctxhx] Error 1

I'm using **AMD64**, so my /lib/libpthread.so.0 is 64 bit.
LD_LIBRARY_PATH=/usr/lib:/usr/lib32:/share/app/oracle/product/10.1.0.3/db_1/lib
and /etc/ld.so.conf contains /lib32

Can anybody help me, please?!! ](*,) :neutral:

---

### Post by ulihoff on 2006-10-18
I've just landed on this site because I was looking for an error during Oracle Installation on Debian. I had the following error in the Installation-Log:

java.lang.reflect.InvocationTargetException
at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
at java.lang.reflect.Method.invoke(Unknown Source)
at oracle.sysman.oip.oipc.oipcr.OipcrRulesEngine.executeRule(OipcrRulesEngine.java:27
at oracle.sysman.oip.oipc.oipcp.OipcpPrereqChecker.executeCheck(OipcpPrereqChecker.java:495)
at oracle.sysman.oip.oipc.oipcp.OipcpPrereqChecker.runChecks(OipcpPrereqChecker.java:450)
at oracle.sysman.oip.oipc.oipcp.OipcpPrereqChecker.executePrereqs(OipcpPrereqChecker.java:351)
at oracle.sysman.oii.oiif.oiifw.OiifwPrereqWCDE$1.run(OiifwPrereqWCDE.java:650)
at java.lang.Thread.run(Unknown Source)
Caused by: java.lang.NullPointerException
at oracle.sysman.oip.oipc.oipch.OipchLinuxVersion.getVersionParts(OipchLinuxVersion.java:533)
at oracle.sysman.oip.oipc.oipch.OipchLinuxVersion.<init>(OipchLinuxVersion.java:77)
at oracle.sysman.oip.oipc.oipch.OipchLinuxGlibcVersion.<init>(OipchLinuxGlibcVersion.java:19)
at oracle.sysman.oip.oipc.oipch.OipchLinuxOSCreator.updateGlibcInfo(OipchLinuxOSCreator.java:207)
at oracle.sysman.oip.oipc.oipch.OipchLinuxOSCreator.updateOSInfo(OipchLinuxOSCreator.java:136)
at oracle.sysman.oip.oipc.oipch.OipchLinuxOSCreator.createOS(OipchLinuxOSCreator.java:120)
at oracle.sysman.oip.oipc.oipch.OipchOSCreator.getOS(OipchOSCreator.java:106)
at oracle.sysman.oip.oipc.oipch.OipchHostCreator.getOS(OipchHostCreator.java:84)
at oracle.sysman.oip.oipc.oipch.OipchHostCreator.build(OipchHostCreator.java:57)
at oracle.sysman.oip.oipc.oipck.OipckKnowledgeSourceFactory.getKnowledgeSourceImpl(OipckKnowledgeSourceFactory.java:239)
at oracle.sysman.oip.oipc.oipck.OipckKnowledgeSourceFactory.getKnowledgeSource(OipckKnowledgeSourceFactory.java:60)
at oracle.sysman.oip.oipc.oipck.OipckKnowledgeSourceLibrary.loadKnowledgeSource(OipckKnowledgeSourceLibrary.java:160)
at oracle.sysman.oip.oipc.oipck.OipckKnowledgeSourceLibrary.getKnowledgeSource(OipckKnowledgeSourceLibrary.java:79)
at oracle.sysman.oip.oipc.oipcr.OipcrRulesEngine.getKnowledgeSource(OipcrRulesEngine.java:563)
at oracle.sysman.oip.oipc.oipcz.OipczOSChecks.checkCertifiedOSVersions(OipczOSChecks.java:69)
... 10 more
java.util.zip.ZipException: invalid entry CRC (expected 0x727d53ff but got 0xa6144445)
at java.util.zip.ZipInputStream.readEnd(Unknown Source)
at java.util.zip.ZipInputStream.read(Unknown Source)
at java.io.FilterInputStream.read(Unknown Source)
at oracle.sysman.oii.oiix.OiixFileOps.copyStream(OiixFileOps.java:1420)
at oracle.sysman.oii.oiij.OiijFastJarExtracter.copyFileFromJar(OiijFastJarExtracter.java:25
at oracle.sysman.oii.oiij.OiijFastJarExtracter.copyJarContents(OiijFastJarExtracter.java:194)
at oracle.sysman.oii.oiij.OiijFastJarExtracter.extract(OiijFastJarExtracter.java:143)
at oracle.sysman.oii.oiij.OiijJarExtractQueue$OiijJarExtractWorker.run(OiijJarExtractQueue.java:341)


**The problem is solved: the zip-file, which I've downloaded from Oracle via lynx was corrupted. Everything worked fine till it crashes at 28% Installation-progress throwing the above error. I checksumed the file and saw a difference to the value on the oracle site. Downloaded again via firefox, Checksum was ok and everything runs fine.**

So if anyone has ever this problem again, read here :)

---

### Post by haunand on 2006-11-05
Hi, I'd like to install Oracle 10gR2 on Unbuntu Edgy Eft too. Did you have to do special preparations like installing additional Ubuntu packages or modify kernel parameters,etc. ?
Did you follow a document / is there a guide how to do it? Please let us know.
Thanks.

Andreas

---

### Post by ridoo on 2006-11-07
I found this really great "[how to install oracle on Ubuntu]("http://www.dizwell.com/prod/node/52")".
Also work for my edgy.

[http://www.dizwell.com](http://www.dizwell.com)

---

### Post by haunand on 2006-11-08
ridoo - thanks a lot, following the document at [http://www.dizwell.com](http://www.dizwell.com) 
the installation of Oracle 10gR2 on Unbuntu Edgy Eft worked like a charm!

:KS

---

### Post by z1hou1 on 2007-02-04
Hi,
I just downloaded 10gR2 - 10201_database_linux32.zip from the Oracle web site - basically the enterprise version. I setup the users, groups and directories and then attempted to run ./runInstaller from the ../database/ directory after unzipping the install zip file.

I get an error to the effect that is is not a valid version of Linux - Red-Hat, Suse etc. Is there any way I can get around this? Any help is appreciated.

I have just installed Ubuntu 6.10 desktop.

Regards,
z1hou1

---

### Post by z1hou1 on 2007-02-04
Please ignore message. I found some answers on [http://www.dizwell.com](http://www.dizwell.com). In this case, I must create the file /etc/redhat-release with the following text

Red Hat Enterprise Linux AS release 3 (Taroon).

Regards,
z1hou1

---

### Post by Hendrixski on 2007-02-05
Yeah, I've installed 10g R1 on Windows, and it was a pain.  I hear it's harder to get on Linux because you have to have a certain kernel release or something.  Even though Oracle does all of their development on Linux, and says that it's the preferred operating system for its database to run on.  Kudos to you for getting it up and running.

I love Linux, and I love Oracle.  Some day I hope to combine the two on a project. I'll keep these links in mind.  Thanks!

---

### Post by g8m on 2007-02-06
I installed oracle-xe_10.2.0.1.0_i386.deb without a problem whatsoever on debian etch, don't know if it's compatible with ubuntu edgy.

---

### Post by Robert Dupuy on 2007-03-03
For some reason, you all didn't answer his question....he said:

I'm using AMD64, so my /lib/libpthread.so.0 is 64 bit.
LD_LIBRARY_PATH=/usr/lib:/usr/lib32:/share/app/oracle/product/10.1.0.3/db_1/lib
and /etc/ld.so.conf contains /lib32

-------

the problem is only this...relink client_sharedlib is creating 32 bit shared libraries.

So, if you didn't install 32 bit glibc-devel and 32-bit gcc.....go back and do it.

You may be on a 64 bit system, but oracle hasn't completely gone 64 bit...that is why you will succeed on compiling oracle (and actually it is a working system)...but it fails on client_sharedlib (and so tools like dbca won't work...).

Anyway...get your 32 bit stuff installed, and you'll find it works.

---

