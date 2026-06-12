---
title: "Get a key state directly from X11?"
date: 2009-05-05
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-05-05
I absolutely have to do this, and my function doesn't seem to work. I know very little about binary, X11 and keyboard scancodes.
```

int get_key_state( Display *dpy, char key )
{
    char keys[32];
    XQueryKeymap( dpy, keys );
    
    int byte = floor( key / 4 );
    int bit = key - ( byte * 4 );
    
    switch( bit )
    {
        case 0:
            return keys[byte] & 0x01;
        
        case 1:
            return keys[byte] & 0x02;
        
        case 2:
            return keys[byte] & 0x04;
        
        case 3:
            return keys[byte] & 0x08;
        
        default:
            break;
    }
    
    printf( "Error! Byte: %d Bit: %d\n", byte, bit );
    return 0;
}

```
I couldn't find much info about X11. And I'm not sure about endianness. Should the switch be inverted?


This is for a console program which is supposed to work only if scroll lock is on.

---

### Post by NintenDave on 2009-05-05
I'm missing something about your mathematics here. First of all, because key and 4 are integer types, that floor function is useless and, in fact, [you're passing the wrong type into it]("http://www.cplusplus.com/reference/clibrary/cmath/floor/") (but it is implicitly cast). Also, if byte is key/4, then bit is key-((key/4)*4), which is key-key, which is 0.

Unfortunately, I don't know enough about Xlib to help you any further than pointing out these logic errors.

---

### Post by crazyfuturamanoob on 2009-05-05
Yeah, floor() is useless. I put it there just to be 100% sure.

And key-((key/4)*4) is not always 0. What if key was 103?
```

103-(103/4)*4 = 103-(25)*4 = 103-100 = 3

```

---

