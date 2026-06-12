---
title: "Quick BASH help"
date: 2007-01-03
forum: Programming Talk
---

### Post by adamonline on 2007-01-03
Hello, I'm trying to get this game-server script to work.  I'm trying to gather all the info I need, and then run the 'launch server' executable to start the server.  I've got everything working okay except where it comes down to launching the server.

```

function run_server
{
    cd $GAME_PATH
    pwd
    exec "srcds_run -console -game cstrike -LAN $var_server_type +map $var_start_map +ip $var_ip_address +maxplayers $var_max_players -autoupdate"
}

```

It changes to the game path okay, all the parameters are okay. The pwd is there for debugging, and shows the game path...  Then when it gets to executing the server I get the output:

```

/home/adam/srcds_1  [COLOR="Gray"](this is from the pwd command)[/COLOR]
./csserver: line 199: exec: srcds_run -console -game cstrike -LAN 0 +map gg_adam_v4 +ip 192.168.1.102 +maxplayers 12 -autoupdate: not found

```

I'm in the right path, and that's exactly what I'd type into the terminal to run the game normally.  So, what do I have to do?

Thanks!

-ADAM

PS, does anyone know of any good tutorials on scripting?  I've come across a few, but they're all really basic.  I want to learn things like reading and writing to external files and things of that nature...  You know, 'intermediate' stuff ;)

---

### Post by amo-ej1 on 2007-01-04
Well the linux documentation project has some great in depth guides on scripting ([www.tldp.org](www.tldp.org))

You have for example: [http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)  : The advanced bash scripting guide 
or [http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html) : Bash for beginners

---

