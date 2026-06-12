---
title: "run cron job second tuesday of the month"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by lance bermudez on 2012-10-20
Found this at a web cite and it says to run in script. Question is will it work? I see it as if the top command in script will only run on the second tuesday and if it is not the second tuesday the 2 command in the script will run so am I reading this right?

#!/bin/bash
if [ $(date +%w) -eq 2 -a $(date +%e) -gt 7 -a $(date +%e) -le 14 ]
then
  <code to be executed here>
else
  <do something>
  exit
fi

---

### Post by spjackson on 2012-10-20
Yes, you are reading this right.

---

