---
title: "Allegro compiling errors"
date: 2008-12-18
forum: Programming Talk
---

### Post by JaxDragon on 2008-12-18
Here is the code I used to compile
```

gcc main.cpp -o output `allegro-config --libs`
```

Here is my source code
```

#include <allegro.h>


int main(){
 
    allegro_init();
    install_keyboard();
    set_gfx_mode( GFX_AUTODETECT, 640, 480, 0, 0);
    
    readkey();
    
    return 0;
    
}   
END_OF_MAIN();

```

Here is the error I get
```

/tmp/ccCA2Xp5.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
```

---

### Post by geraldm on 2008-12-18
gcc is a  C compiler
g++ is for C++ compiles.

---

