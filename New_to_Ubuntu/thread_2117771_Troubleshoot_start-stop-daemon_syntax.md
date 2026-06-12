---
title: "Troubleshoot start-stop-daemon syntax"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by PlayWithFire on 2013-02-19
I am having problems getting [maraschino]("http://www.maraschinoproject.com/") to run on boot. Executing [FONT="Courier New"][COLOR="Blue"]python Maraschino.py --port=8085[/COLOR][/FONT] works well, so it's gotta be the init script. I believe this line is to blame
[FONT="Courier New"][COLOR="Blue"]start-stop-daemon -o -d /opt/maraschino -c pasha --start --background --pidfile /var/run/maraschino/maraschino.pid  --make-pidfile --exec /usr/bin/python -- python Maraschino.py --port=8085[/COLOR][/FONT] 
Do you see anything wrong with it?

---

