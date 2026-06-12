---
title: "C + gtk"
date: 2011-10-04
forum: Programming Talk
---

### Post by Ghostmn on 2011-10-04
Hello, I was wondering if anyone with Experience in Gtk could tell me how to properly declare a structure, and pass it by reference in a callback function.

Currently I'm receiving a segmentation fault while trying to access data in the structure.

I'm new to GTK,but I do have experience with C,C++,GO, and Java.

Shorten code.
```

void New_Game() {

   GtkWidget *window;
   //declared in a header.
   struct planets data;

   generic(window,&data);
   
}
void generic(GtkWidget *window,struct planets *data) {
    GtkWidget *button;

    g_signal_connect(G_OBJECT(button),"clicked",
                              G_CALLBACK(derp),data);

}
void derp(GtkWidget *widget,struct planets data) {
    g_print("%s",data->planet_name);
}

```The source code is attached in a tarball if you want to see the actual source. Compile and run, click new game, and click universe. That gives the segmentation fault.

---

### Post by cgroza on 2011-10-04
I think it is segfaulting because you never initialize your structure before you pass it to your function.
```

struct planets {
        GtkObject Parent;
        int locations[5][300];
        int current_location;
        int fields[5][300];
        int first_world[2][1];
        char *planet_name[5][300];
};

```

You never allocate space for planet_name and never assign anything to Parent.

---

### Post by Ghostmn on 2011-10-04
> **cgroza said:**
> I think it is segfaulting because you never initialize your structure before you pass it to your function.
```

struct planets {
        GtkObject Parent;
        int locations[5][300];
        int current_location;
        int fields[5][300];
        int first_world[2][1];
        char *planet_name[5][300];
};

```You never allocate space for planet_name and never assign anything to Parent.
  
I've never had to initialize a structure. How would I initialize it?

I removed parent as I didn't use it to begin with.

I thought planet_name already had already been allocated. The code in universe had came from Generic and it was able to access the data found in planet_name without segfaulting. It was only when I split the code up into two different functions that I began receiving segfaults.

EDIT1: Doesn't the structure get initialized when I set data to its members?

---

### Post by cgroza on 2011-10-04
The planet_name member is a pointer to an array, not an array, so it is your responsibility to give it some valid space to point to.
The rest of the members contain the trash on the stack, you can use memset to set that memory to 0.

---

### Post by Ghostmn on 2011-10-04
> **cgroza said:**
> The planet_name member is a pointer to an array, not an array, so it is your responsibility to give it some valid space to point to.
The rest of the members contain the trash on the stack, you can use memset to set that memory to 0.

Would I allocate like this, since it's a multidimensional array?
```

    int a;

    data.planet_name = (char**)malloc( sizeof(char *) * 5);
    for (a=0;a<5;a++)
        data.planet_name[a] = (char*)malloc(sizeof(char)*300);


```

---

### Post by cgroza on 2011-10-05
It seems fine to me. You can make a small test by assigning something to it and then trying to access it.

---

### Post by nvteighen on 2011-10-05
No, this is much simpler... If you just want a two dimensional matrix, you should declare the planet_name member as this:

```

char planet_name[5][300]; // NO *planet_name!!

```

Even though I cannot think of any context where a planet's name should be represented as a two dimensional matrix... A simple char array (= "string" in C) would be enough.

Anyway, the problem is that you were declaring a pointer to a two-dimensional matrix... a pointer is just 4-bytes long and in this case, would have stored a completely random value until you bound it to a valid memory place (e.g. using malloc). But again, doing that indirection seems to make very little sense in this context, because dynamic allocation is only used when you don't know the size in memory of an object at compile-stage, but at runtime. Here, you're already telling us that you want a 5x300 matrix for some reason, so you know the size at compile-stage.

(There's an exception to the above: when you know the size but it's so huge that it doesn't fit into the stack... so you have to use the heap)

---

### Post by Ghostmn on 2011-10-05
> **nvteighen said:**
> No, this is much simpler... If you just want a two dimensional matrix, you should declare the planet_name member as this:

```

char planet_name[5][300]; // NO *planet_name!!

```Even though I cannot think of any context where a planet's name should be represented as a two dimensional matrix... A simple char array (= "string" in C) would be enough.

Anyway, the problem is that you were declaring a pointer to a two-dimensional matrix... a pointer is just 4-bytes long and in this case, would have stored a completely random value until you bound it to a valid memory place (e.g. using malloc). But again, doing that indirection seems to make very little sense in this context, because dynamic allocation is only used when you don't know the size in memory of an object at compile-stage, but at runtime. Here, you're already telling us that you want a 5x300 matrix for some reason, so you know the size at compile-stage.

(There's an exception to the above: when you know the size but it's so huge that it doesn't fit into the stack... so you have to use the heap)

I realized this a few hours ago. The amount of planet_names is relative to how many planets there are going to be.

---

### Post by nvteighen on 2011-10-06
> **Ghostmn said:**
> I realized this a few hours ago. The amount of planet_names is relative to how many planets there are going to be.

Hm... wouldn't it be much better to create a "planet" structure and then stuff all planets into a linked list? That way, the structure would be clearer and it'd be much easier to manipulate each planet separately. Since you're using GTK+, you're already using GLib, so check the GList data structure, which may prove very useful for this (instead of reimplementing a linked list yourself).

---

