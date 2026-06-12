---
title: "String Processing in Python"
date: 2008-02-29
forum: Programming Talk
---

### Post by BurnTheSource on 2008-02-29
Hi all,

So, I feel really guilty for having to ask this, but I'm having a lot of trouble wrapping my head around Python's string manipulation methods. I'm accustomed to programming in Perl, and I figured as a "step into" Python I would recode one of my Perl scripts into Python.

So, here's the beef of it. I have a script that connects to a network socket, consumes the data coming in in 2048 byte chunks, and parses it according to a designated "end of line" character.

In Perl, I currently do this using substr and index. I can't, however, seem to figure out how to make it work in Python (despite fighting with it for a few days). I've been poking around the web for a little while and haven't been able to find any examples to base my changes on.

Anyone willing to offer a little help?

Here's what I had in Perl (where nBytes represents the most recent "chunk" of data from the socket).
```

if ($nBytes)
{
     $buffer .= $msg;
     my $tail = index $buffer, $EOM;
     while ( $tail >= 0 )
    {
        my $length = $tail + 1;
        my $inMsg = substr($buffer,0,$length);
        printf substr($inMsg,1) unless ($inMsg =~ /^H/);
        $wantResp = 1 if ($inMsg =~ /^H/);
        substr($buffer,0,$length) = "";

        $tail = index $buffer, $EOM;
    }
}

```

Now, please be patient with me here because my Python is admittedly horrible (I'm still learning).

Here's the Python:
```

if data:
    buffer = ""
    buffer += data
    print buffer
    tail = index(buffer, EOM)
    while tail >= 0:
        length = tail + 1;
        inMsg = data[0:length].strip()
        print inMsg
        lead = exp.match(inMsg)
        if lead: gimme_heart = 1

        tail = index(data, EOM)

```

I think I've wrapped myself around in circles and now I have no idea where I am anymore.

Anyone willing to offer a little assistance? I'm really starting to feel like a moron.

---

### Post by ghostdog74 on 2008-02-29
1) [Python socket programming howto]("http://www.amk.ca/python/howto/sockets/")
2) [example straight from the Python doc]("http://docs.python.org/lib/socket-example.html")

the equivalent of substr in Python is just indexing/slicing eg thestring[0:10] 
the equivalent of index() in Python is also index() eg thestring.index("something")

---

### Post by BurnTheSource on 2008-02-29
Yeah, the socket portion of it I have down pat. The issue here is that the data itself (line for line) is not 2048 bytes. In that 2048 I may have 10 lines, or 20 lines (the data is somewhat variable).

The only thing defining one "line" from another in the block of data I receive is the EOL character (0x0A). I'll try the string.index again and see if I can figure it out that way.

Basically I read 2048 bytes in, parse out as many "lines" as possible, constantly cutting down the data variable until there is nothing left, then I go on and get the next chunk of data in from the socket.

---

### Post by pmasiar on 2008-02-29
Maybe instead of forcing Perl logic on it, you may read string processing from ie "Dive Into Python" book?

And logic is different in your code, in perl variant you don't clean buffer using  buffer = "".

---

### Post by BurnTheSource on 2008-02-29
Sounds good. I'll do some more research and try to push the logic around. Thanks for the help.

---

