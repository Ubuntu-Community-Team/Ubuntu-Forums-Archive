---
title: "C GTK+ Program Advice"
date: 2009-12-19
forum: Programming Talk
---

### Post by lewisforlife on 2009-12-19
I am pretty new to C programming as well as GTK+.  Here is my program to find out if a number is prime or not.  Right now it is a GUI interface, currently the results are outputed to the terminal:

prime_directive.c

```

#include <gtk/gtk.h>
#include "pd.h"

static gboolean delete_event (GtkWidget *widget, GdkEvent *event, gpointer data)
{
    return FALSE;
}

static void destroy (GtkWidget *widget, gpointer data)
{
    gtk_main_quit();
}


int main (int argc, char *argv[])
{
    GtkWidget *window;
    GtkWidget *table;
    GtkWidget *label;
    GtkWidget *entry;
    GtkWidget *button;
    
    gtk_init (&argc, &argv);
    
    window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
    gtk_widget_set_size_request (GTK_WIDGET (window), 250, 85);
    gtk_window_set_title (GTK_WINDOW (window), "Prime Directive");
    g_signal_connect (G_OBJECT (window), "delete_event", G_CALLBACK (delete_event), NULL);
    g_signal_connect (G_OBJECT (window), "destroy", G_CALLBACK (destroy), NULL);
    
    table = gtk_table_new (3, 1, TRUE);
    gtk_container_add (GTK_CONTAINER (window), table);
    
    label = gtk_label_new ("Enter a Possible Prime");
    gtk_table_attach (GTK_TABLE (table), label, 0, 1, 0, 1, GTK_EXPAND, GTK_EXPAND, 0, 0);
    gtk_widget_show (label);
    
    entry = gtk_entry_new ();
    gtk_table_attach (GTK_TABLE (table), entry, 0, 1, 1, 2, GTK_FILL, GTK_FILL, 10, 0);
    gtk_widget_show (entry);
    
    button = gtk_button_new_with_label ("Check");
    g_signal_connect (G_OBJECT (button), "clicked", G_CALLBACK (check_possible_prime), (gpointer) entry);
    gtk_table_attach (GTK_TABLE (table), button, 0, 1, 2, 3, GTK_FILL, GTK_FILL, 10, 3);
    gtk_widget_show (button);
    
    gtk_widget_show (table);
    gtk_widget_show (window);
    
    gtk_main();
    
    return 0;
}

```

pd.h
```

void check_possible_prime (GtkWidget *widget, GtkWidget *entry);
int check_prime (int iNum);

```

primecheck.c
```

#include <stdio.h>
#include <stdlib.h>
#include <gtk/gtk.h>
#include "pd.h"

int check_prime (int iNum)
{
    int i = 3;
    int iIsPrime = 1;
    
    while (i <= (iNum / 2))
    {        
        if (iNum % i == 0)
        {
            iIsPrime = 0;
            break;
        }
        
        i += 2;
    }
    
    return iIsPrime;
}


void check_possible_prime (GtkWidget *widget, GtkWidget *entry)
{
    int iEntry, iEvenOdd;
    int iIsPrime;
    
    const gchar *entry_text;
    entry_text = gtk_entry_get_text (GTK_ENTRY (entry));
    
    iEntry = atoi (entry_text);
    
    iEvenOdd = iEntry % 2;
    
    switch (iEvenOdd)
    {
        case 0:
            printf ("Primes can only be odd, please enter an odd number!\n");
            break;
        
        case 1:
            iIsPrime = check_prime (iEntry);
            
            if (iIsPrime == 1)
                printf ("You found a prime number!\n");
            else
                printf ("Sorry, try again...\n");
            
            break;
    }
}

```

Basically I just want to know, is this how you would go about writing a program of this sort?  Am I using proper coding technique in C?  Is there any way I can make this more efficient?  I am going to be working on a much bigger project and want to make sure I have the right technique.  Thanks for your advice!

---

### Post by MadCow108 on 2009-12-19
Your algorithm is very ineffective. you only have to check up to sqrt(number)

also there are better ways to check if something is prime:
[http://en.wikipedia.org/wiki/Primality_test#Fast_deterministic_tests](http://en.wikipedia.org/wiki/Primality_test#Fast_deterministic_tests)

but if the work implementing this is worth it depends on your requirements.
if you only need to check integers it may be easiest and fastest to just check a table of all primes till 2^31-1

---

### Post by lewisforlife on 2009-12-19
> **MadCow108 said:**
> Your algorithm is very ineffective. you only have to check up to sqrt(number)

also there are better ways to check if something is prime:
[http://en.wikipedia.org/wiki/Primality_test#Fast_deterministic_tests](http://en.wikipedia.org/wiki/Primality_test#Fast_deterministic_tests)

but if the work implementing this is worth it depends on your requirements.
if you only need to check integers it may be easiest and fastest to just check a table of all primes till 2^31-1

Thanks, I will fix it so that it only checks up to sqrt(number).  Also, when you said that if I only need to check integers it may be best to have a table of all primes.  I would like to check higher than integers, what data types would allow me to check bigger numbers?

---

### Post by MadCow108 on 2009-12-20
on 64 bit machines you can use 64 bit integers efficiently
the C99 type would be unsigned long long or uint64_t defined in inttypes.h
they go up to 2^64-1 but are slower on 32 bit machines.

for even higher numbers you need a bignumber library like gmp ([http://gmplib.org/](http://gmplib.org/)) or cln ([http://www.ginac.de/CLN/](http://www.ginac.de/CLN/))
the c++ library cln even has a Miller-Rabin primality test (probabilistic) built in:
[http://www.ginac.de/CLN/cln_4.html#SEC36](http://www.ginac.de/CLN/cln_4.html#SEC36)

note that primality test gets quite slow for very big numbers. because of that one often uses non-deterministic methodes as mentioned in the wiki article I posted earlier.

---

### Post by nvteighen on 2009-12-20
There's a fundamental error in your code, much more important IMO than the algorithm uneffectiveness.

You're mixing the UI with your implementation code. No. check_possible_prime should be placed at prime_directive.c. Think it this way: Your backend is like a shell and the UI frontend is a user that calls stuff into that shell... (ok, the UI frontend will actually create another "shell" for the real user, but that's the idea about interfaces)

In your case, the mistake is simple and you can live along by cutting-and-pasting that function from one file to another. But please get into the habit of strictly separating UI from the rest, because in bigger projects it can become a mess if you do it otherwise... Also, by separating everything UI programming gets actually much easier: You'll know where is everything and doing what.

---

### Post by lewisforlife on 2009-12-20
> **nvteighen said:**
> There's a fundamental error in your code, much more important IMO than the algorithm uneffectiveness.

You're mixing the UI with your implementation code. No. check_possible_prime should be placed at prime_directive.c. Think it this way: Your backend is like a shell and the UI frontend is a user that calls stuff into that shell... (ok, the UI frontend will actually create another "shell" for the real user, but that's the idea about interfaces)

In your case, the mistake is simple and you can live along by cutting-and-pasting that function from one file to another. But please get into the habit of strictly separating UI from the rest, because in bigger projects it can become a mess if you do it otherwise... Also, by separating everything UI programming gets actually much easier: You'll know where is everything and doing what.

I see your point, primecheck.c should not have to have gtk.h included because it should not have any interface code in it.  This is the kind of stuff I was looking for advice on, because I know soon I will be working on a big project, and I want to make sure I am using correct conventions.

---

### Post by lewisforlife on 2009-12-20
> **MadCow108 said:**
> on 64 bit machines you can use 64 bit integers efficiently
the C99 type would be unsigned long long or uint64_t defined in inttypes.h
they go up to 2^64-1 but are slower on 32 bit machines.

for even higher numbers you need a bignumber library like gmp ([http://gmplib.org/](http://gmplib.org/)) or cln ([http://www.ginac.de/CLN/](http://www.ginac.de/CLN/))
the c++ library cln even has a Miller-Rabin primality test (probabilistic) built in:
[http://www.ginac.de/CLN/cln_4.html#SEC36](http://www.ginac.de/CLN/cln_4.html#SEC36)

note that primality test gets quite slow for very big numbers. because of that one often uses non-deterministic methodes as mentioned in the wiki article I posted earlier.

Thanks, I will look into using gmplib for bigger numbers.  I was thinking, just for fun working on a distributed computing project to search for prime numbers, GMP library looks like it will do the trick.  I know that this already exists, I have heard of the gimps prime number search, but it will be good experience for me to try this on my own.
(lol, this gets kind of confusing, I am using gimp toolkit as a interface, gmp library for big numbers, and the distributed computing project to find prime numbers is called gimps, is there any relation between the 3?)

Also, I was thinking, if I use the gmp library to deal with really big numbers, say I have a million digit number in a text file that I want to hand different pieces of work out to different computers to check if it is prime or not.  Would I load the whole million digit number into memory to do the check, or is there a better way?  Will I have enough memory to do this on a modern computer?

---

### Post by MadCow108 on 2009-12-20
a pc with 4 gb free ram can hold numbers up to 2^34359738368 (under the assumption of zero overhead storage)
the largest known prime is in the region of 2^42643801
so the storage of the actual number will be no problem (but lookup tables of course may be, but thats algorithm dependent)

---

