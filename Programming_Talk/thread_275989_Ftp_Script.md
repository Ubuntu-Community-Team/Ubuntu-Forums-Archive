---
title: "Ftp Script"
date: 2006-10-12
forum: Programming Talk
---

### Post by dyol on 2006-10-12
Quote:
Originally Posted by amo-ej1 View Post
@chi_n_z: when you want to do load tests about something you will _always_ try to isolate what you are testing from the rest, so your test is worthless if you don't do it on a dedicated interface.

@amo-ej1:thanx again i managed to direct some of the output but failed to send this part[quote]
real 0m2.397s
user 0m0.000s
sys 0m0.004s
[quote]
yeh these are load tests-but i thot since iwas comparing file transfer in two different networks[PLC and ethernet]will it not make sense to also compare the time it takes to download file A in both both networks-having said that how would one isolate bandwith-how one include bandwith in the script-the other thing there is stuff iam failing understand in the output given by the script--the stuff in red
Quote:
--22:08:21-- [ftp://1.2.5.1/Hustling.doc](ftp://1.2.5.1/Hustling.doc)
=> `Hustling.doc.5'
Connecting to 1.2.5.1:21... connected.
Logging in as xxxx ... Logged in!==> SYST ... done. ==> PWD ... done.
==> TYPE I ... done. ==> CWD not needed.
==> PASV ... done. ==> RETR Hustling.doc ... done.
Length: 69,120 (68K) (unauthoritative)

0K .......... ..74% 31.19 KB/s
50K .......... ..100% 32.48 KB/s

22:08:24 (31.52 KB/s) - `Hustling.doc.5' saved [69120]
Reply With Quote

---

