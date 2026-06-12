---
title: "GTK SlideShow"
date: 2011-11-27
forum: Programming Talk
---

### Post by sgtlaugh on 2011-11-27
How do I create a slideshow with gtk? I've written a next function which displays the next image but it's not working:

```
void start_slide()
{
    for(; ;){
        
        g_usleep(1000000); // Wait for 1 second
        show_next(); // Displays the next image
    }
}
```

Please help. Thank you.

---

### Post by crdlb on 2011-11-27
You're blocking the whole program when you sleep like that. Instead, use g_timeout_add or g_timeout_add_seconds to make the mainloop call a function after the specified time interval. In this case, you should probably use the _seconds variant for power efficiency.

---

