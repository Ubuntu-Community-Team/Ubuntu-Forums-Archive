---
title: "having a problem with my irc bot in perl"
date: 2009-02-07
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-02-07
[PHP]#!/usr/bin/perl

###################
# A basic irc bot #
###################

use Bot::BasicBot;

$bot = Bot::BasicBot->new(
        server  => "irc.freenode.net",
        port    => "6667",
        channels=> ["#ubuntu-programming"],
        nick    => "bot",
        alt_nicks=> ["bot"],
        username => "bot",
        name     => "bot",
        ignore_list => [],
        charset => "utf-8");

$bot->run();
[/PHP]

it runs...but it cannot connect to freenode...ive tried a bunch of different ports...heres the out put

```
 perl bot.plx 
Trying to connect to server irc.freenode.net
Server error occurred! Closing Link: 127.0.0.1 (Connection Timed Out)
Lost connection to server irc.freenode.net.
Trying to connect to server irc.freenode.net

```

help please?

---

