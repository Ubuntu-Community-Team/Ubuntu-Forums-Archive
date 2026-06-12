---
title: "Allegro and Code Blocks"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by yang925goes on 2008-09-29
I have Kubuntu 8.04 with GNOME installed. I installed code blocks to start programing again in c++. The usaul text based programs compile and link fine. so i thought i would start getting into games and graphic modes. so i decided to use Allegro. i downloaded the source made and installed it fine. i couldnt get it to work with code blocks so i downloaded and install the .deb packages from the repository. I added `allegro-config --libs --static` to other linker options. When i try to compile
> 
#include <allegro.h>
int main(void)
{
  allegro_init();

  allegro_message("Allegro version = %s\n", allegro_id);

  return 0;
}
END_OF_MAIN()


it compiles fine and i get tons of linker errors, undefiend refrence to functions probbley included in allegro.h ! i am assuming this means i didnt link in the libaries correctly. so when i go to added the libary to link libaries i search for /usr/lib/allegro/*.a but there is none.. only a bunch of *.so

What do i do!

---

### Post by nowshining on 2008-09-29
the .so items are the libs :) ie: the libraries... and u can also try /usr/local/lib/ alas did u do a sudo ldconfig after compiling and installing the program u compiled??

---

