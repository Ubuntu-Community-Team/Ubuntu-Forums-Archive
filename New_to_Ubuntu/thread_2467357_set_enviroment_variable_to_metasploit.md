---
title: "set enviroment variable to metasploit"
date: 2021-09-24
forum: New to Ubuntu
---

### Post by danielmu on 2021-09-24
hello i have the following question. i want to create a connection between metasploit and the tool TheFatRat. although i have both programs installed the program can't find the access to metasploit. i think i have to set an environment variable. but i don't know how


[HR][/HR]
#daniel@da-m82:~/TheFatRat$ sudo ./chk_tools 
--------- TheFatRat tools version check---------- 
---- --------------------------------------------- 
* - Checking Netcat (Net Check)...............[&#10004;] 
* - Checking Xterm (Terminal).................[&#10004;] 
* - Checking Dig (Dns-Util)...................[&#10004;] 
* - Checking mono-mcs (compiler)..............[&#10004;] 
* - Checking Gcc (compiler)...................[&#10004;] 
* - Checking Apache2 (Web Server).............[&#10004;] 
* - Checking Gnome Terminal (Terminal)........[&#10004;] 
* - Checking Upx (File Compressor)............[&#10004;] 
* - Checking Ruby (Programming)...............[&#10004;] 
* - Checking Gem (Ruby modules installer).....[&#10004;] 
* - Checking nokogiri (Ruby module)...........Error loading RubyGems plugin "/var/lib/gems/2.7.0/plugins/yard_plugin.rb": cannot load such file -- /tmp/bundler20210924-25520-loag3tyard-0.9.26/gems/yard-0.9.26/lib/rubygems_plugin.rb (LoadError) 
[&#10004;] 
* - Checking Openssl (Certificates)...........[&#10004;] 
* - Checking Python3 (Programming)............[&#10004;] 
* - Checking Python-pip3 (Module Installer)...[&#10004;] 
* - Checking names (python module)............[&#10004;] 
* - Checking Build-Essential (Cross Compiler).[&#10004;] 
* - Checking Python-Dev (Compiler)............[&#10004;] 
* - Checking lib32z1 (apk Req.)...............[&#10004;] 
* - Checking lib32ncurses5 (apk Req.).........[&#10004;] 
* - Checking lib32stdc++6 (apk Req.)..........[&#10004;] 
* - Checking Jarsigner (apk Req.).............[&#10004;] 
* - Checking Keytool (apk Req.)...............[&#10004;] 
* - Checking Unzip (Unpacker).................[&#10004;] 
* - Checking Zipalign (Apk Req.)..............[&#10004;] 
* - Checking Mingw 64 Bit (Compiler)..........[x] Not Found 
 [HR][/HR]
------------Solution ------------- 
Step 1 - Run Setup from fatrat 
 
chmod +x setup.sh && ./setup.sh 
 
---------------------------------- 
* - Checking Mingw 32 Bit (Compiler)..........[x] Not Found 
 
------------Solution ------------- 
Step 1 - Run setup from fatrat 
 
chmod +x setup.sh && ./setup.sh 
---------------------------------- 
 
 
* - Checking Dx (Apk Req.)....................[&#10004;] 
* - Checking Aapt (Apk Req.)..................[&#10004;] 
* - Checking Apktool (Apk Req.)...............[&#10004;] 
* - Checking Baksmali (Apk Req.)..............[&#10004;] 
* - Checking Metasploit-Framework (msfc)......[x] Solution: apt-get install metasploit-framework 
Install using kali repository 
* - Checking Metasploit-Framework (msfv)......[x] Solution: apt-get install metasploit-framework 
Install using kali repository 
* - Checking Backdoor Factory (exe backdoor)..[&#10004;] 
* - Checking Searchsploit (exploit db)........[x] Solution: apt-get install exploitdb 
Install using kali repository/Ignore in case manually installed #

[HR][/HR]

---

### Post by coffeecat on 2021-09-24
From TheFatRat github page:

> TheFatRat is an exploiting tool which compiles a malware with famous payload, and then the compiled maware can be executed on Linux , Windows , Mac and Android. TheFatRat Provides An Easy way to create Backdoors and Payload which can bypass most anti-virus.



Really?

Thread closed.

---

