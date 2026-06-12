---
title: "Bitlbee 1.2.8-1 + Irssi to connect to Facebook?"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by honeybear on 2012-02-06
Hi, 

I would like to connect to facebook, but unfortunately I receive this error msg: 

```
ii  bitlbee                                  1.2.8-1                            An IRC to other chat networks gateway

```

```



11:16 <@josh729> account add jabber Myfacebookaccount@chat.facebook.com
11:16 <@root> Not enough parameters given (need 4).
11:17 <@josh729> account add jabber Myfacebookaccount@chat.facebook.com
11:17 <@root> Not enough parameters given (need 4).
11:17 <@josh729> account add jabber Myfacebookaccount@chat.facebook.com ''XXXX''
11:17 <@root> Account successfully added
11:17 <@josh729> account facebook set  Myfacebookaccount Myfacebookaccount 
11:17 <@root> Unknown command: account facebook. Please use help commands to get a list of available commands.
11:17 <@josh729> account facebook set  nick_source Myfacebookaccount 
11:17 <@root> Unknown command: account facebook. Please use help commands to get a list of available commands.
11:18 <@josh729> account facebook set  Myfacebookaccount Myfacebookaccount 
11:18 <@root> Unknown command: account facebook. Please use help commands to get a list of available commands.
11:18 <@josh729> account off
11:18 <@root> Deactivating all active (re)connections...
11:18 <@josh729> account on
11:18 <@root> Trying to get all accounts connected...
11:18 <@root> yahoo - Logging in: Connecting
11:18 <@root> jabber - Logging in: Connecting
11:18 <@root> jabber - Logging in: Connected to server, logging in
11:18 <@root> jabber - Logging in: Converting stream to TLS
11:18 <@root> jabber - Logging in: Connected to server, logging in
11:18 <@root> yahoo - Logging in: Logged in
11:18 <@root> jabber - Couldn't log in: Authentication failure
11:18 <@root> jabber - Logging in: Signing off..
11:18 <@josh729> account off
11:18 <@root> Deactivating all active (re)connections...
11:18 <@root> yahoo - Signing off..
11:19 <@josh729> account fb set Myfacebookaccount Myfacebookaccount
11:19 <@root> Unknown command: account fb. Please use help commands to get a list of available commands.


```

Would you eventually by chance know how to make this working (myfacebookacount is my username into facebook)

thank you



why it does not identify? 
> 
21:29 <@root> If you already have an account on this server, just use the identify command to identify yourself.
21:29 -!- Irssi: Join to &bitlbee was synced in 0 secs
21:29 <@josh729> account list
21:29 <@root> End of account list
21:29 <@josh729> identify
21:29 <@root> Not enough parameters given (need 1).

identify password or identify pseudo ?

---

