---
title: "Perl IO::Socket IRC Bot"
date: 2010-06-02
forum: Programming Talk
---

### Post by miniCruzer on 2010-06-02
I've got a framework for an IRC Bot in Perl. It connects to the network, communicates with the server, identifies to NickServ, and Opers up.

However, its main purpose is to emulate QuakeNet / O Services 'R' bot, which allows you to request other services for your channel, (SpamServ, Q, etc.). I use several other services such as StatServ, infoServ, among other customized services.

This bot needs to be able to act like a service. A user will /msg R HELP and the bot will notice back all of the usable commands. I've done some searching, and I can't seem to find how to get this part to work. I think it requires the use of another module.

As of now with IO::Socket, it can only reply in basic terms. If it sees a word anywhere in the IRC context, it can message a certain channel, but it can't reply to its source.

For example, if it sees PING, it sends PONG to the server.
```

while (my $input = <$sock>) {
    chomp $input;
    if ($input =~ /^PING(.*)$/i) {
        print $sock "PONG $1\r\n";
    }
    else {
        print "$input\n";
    }
}

```

---

