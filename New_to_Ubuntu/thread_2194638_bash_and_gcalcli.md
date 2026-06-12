---
title: "bash and gcalcli"
date: 2013-12-19
forum: New to Ubuntu
---

### Post by lance bermudez on 2013-12-19
I have a bash script with
#! /bin/bash
echo "quick 'Record another BASH video tomarrow at time'";
echo "quick '5pm 10/31 trick or treat'";
read name;
gcalcli --user Username --pw password $name

I get "Error: invalid event text"

help

---

### Post by steeldriver on 2013-12-19
What exactly is the purpose of the echoes / read? are you trying to construct a command argument for gcalcli? if so wouldn't that be something like

```

cmd="quick '5pm 10/31/2014 trick or treat'"
gcalcli --user Username --pw password "$cmd"

```

---

### Post by lance bermudez on 2013-12-19
Below is how I finily got my script to  work and FYI the echo are for me to remember how to use the script. I do not know how to make a man page for may script so I jus echo things I want to remember.

#! /bin/bash
echo "##########################################"
echo "### How You Put Stuff in Google Calendar ###"
echo "##########################################"
echo "5pm 10/31 trick or treat        ### Time Month/Day Event   ###"
echo "##########################################"
echo  
echo "##########################################"
echo "Tomarrow 8am Doctor Who         ### Tomarrow Time Event    ###"
echo "##########################################"
echo  
echo "##########################################"
echo "fri 12am event Does day in week ### Day of Week Time Event ###"
echo "##########################################"
echo  
echo "##########################################"
echo "7pm S.H.I.E.L.D.                ### Does today unless time ###" 
echo "                                    has passed then does   ###"
echo "                                    that time tomarrow     ###";
read ;
gcalcli quick "$REPLY"

---

