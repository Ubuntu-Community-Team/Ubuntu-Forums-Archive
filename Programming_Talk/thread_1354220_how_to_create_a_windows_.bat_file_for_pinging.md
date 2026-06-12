---
title: "how to create a windows *.bat file for pinging"
date: 2009-12-13
forum: Programming Talk
---

### Post by lance bermudez on 2009-12-13
I was told that their is a way to create a ping.bat file that will ping

Not the real addresses)
192.168.1.1
192.168.1.2

and so on leaving the command line window open. the ping.bat file would creat a text file letting me know which address did not send a replay. I don't know how to do this. Please help me. I also need this file to work on windows xp and windows 7.

---

### Post by nelfin on 2009-12-13
Logic is not something that Windows batch files have been traditionally very good at, the following snippet will tell you which addresses drop packets (out of the four that ping.exe normally sends).

```
@echo off
if %1.==. goto usage

:loop
if %1.==. goto check
echo Pinging %1...
ping %1 > %1.ping
shift
goto loop

:check
echo.
echo Dropped packets > results.txt
for %%F in (*.ping) do find "Request timed out" %%F /c >> results.txt
goto cleanup

:usage
echo usage: %0 addr [addr, ...]
goto end

:cleanup
if exist results.txt type results.txt
if exist *.ping del *.ping

:end

```

---

### Post by lance bermudez on 2009-12-14
how do i set up the file. all i know is that to open notepad and save it a *.bat. the addreass i need pinged are 172.18.24.120 - 172.18.24.127. How do i use what you gave me? I don't get it i'm a complet noob to this. thank you for your help.

---

### Post by lance bermudez on 2009-12-14
below is what i have working however i was wantting to know if their was a was for 
if %ERRORLEVEL%== 1 ping -n 1 172.18.24.120 >> c:\c\response.txt
to just write schwartz in the response.txt for the error of no ping 

@echo off

del response.txt

ping -n 1 172.18.24.120 
if %ERRORLEVEL%== 1 ping -n 1 172.18.24.120 >> c:\c\response.txt

ping -n 4 172.18.24.122
if %ERRORLEVEL%== 1 ping -n 4 172.18.24.122 >> c:\c\response.txt

pause

echo .........Below is what did not ping

@echo off
type response.txt

pause

---

### Post by nelfin on 2009-12-14
Sorry for not explaining better, it was a bit of a rush job.

The idea was that you'd save it as a .bat file (say multiping.bat) and then run it from a commandline a la 
```
multiping.bat ipaddr1 ipaddr2 ...
```

If a batch file is what you really need then all this should be a good start. However, if determining whether an address (or a range of addresses, an subnet of addresses, or the entire internet) is up or not, then allow me to suggest using nmap instead (available from [http://nmap.org](http://nmap.org)) which will do what you're looking for perfectly, and a lot faster too.

For what you want (checking whether 172.18.24.120 - 172.18.24.127 are up)
```
nmap -sP 172.18.24.120-127
``` should do the trick

---

### Post by lance bermudez on 2009-12-15
the one I have works fine I also like yours. However i want it to hold the address so i don't have to look them up I also would like 172.18.24.120 to display as schwartz in the response.txt. That way i know which room is down instead of again looking up the address. Thank for taking the time you have been most helpful.

---

### Post by lance bermudez on 2009-12-15
I have 3 file that do what i want thank you for all of your help

1 file start.bat
@echo off

start cmd.exe /k locrout.bat

start cmd.exe /k pingadd.bat addr 172.18.24.120 172.18.24.121 172.18.24.122 172.18.24.123 172.18.24.124 172.18.24.125 172.18.24.126 172.18.24.127 

second file is above from nelfin i called mine pingadd.bat

3 file is call locrout.bat

@echo off

type location.txt

Location.txt is a file that have room # of whare the address go

---

