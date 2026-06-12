---
title: "Perl: rtmpdump pipe to vlc"
date: 2011-06-17
forum: Programming Talk
---

### Post by Armarr on 2011-06-17
I'm trying to get ustream to play in vlc.
This code outputs it to a file, which works fine: [https://gist.github.com/634461](https://gist.github.com/634461)
but I though I could just modify the code to pipe it trough with "&#448; vlc" but it's outputting it to the terminal itself resulting in pages of gibberish

Atm I have only modified line 27 to:
```
    my $command = 'rtmpdump -v -r "'.$video_url.'" -a "ustreamVideo/'.$video_id.'" -f "LNX 10,0,45,2" -y "streams/live" --stop '.$stop.**'&#448; vlc';**
```

---

### Post by Armarr on 2011-06-19
*bump*
can't be that hard to do, can it?

---

