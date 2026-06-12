---
title: "Can't open TOR"
date: 2014-05-15
forum: New to Ubuntu
---

### Post by quadrplax on 2014-05-15
When I click on start-tor-browser, it opens in gedit. It has execute permissions. I guess that's all I need to say.

---

### Post by Kingsrookie on 2014-05-15
All you need to do is open terminal and change directory to where start-tor-browser resides.

On my pc its /home/(Username Here)/Downloads/tor-browser_en-us

then type ./start-tor-browser and it will open right up. 
Another method is to use the sh command.
sh start-tor-browser

Both methods will work to open the shell script. The sh command is the command used to actually run the scripts but ./ accomplishes the same function.
The file you are opening is a shell script. When you click it to open with gedit, you can only change properties.

Try it out! If it works you can mark the thread as solved!

---

### Post by quadrplax on 2014-05-16
ah, didn't know the "./" thing.

---

