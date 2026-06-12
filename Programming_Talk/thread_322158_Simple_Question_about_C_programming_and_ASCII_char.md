---
title: "Simple Question about C programming and ASCII characters"
date: 2006-12-20
forum: Programming Talk
---

### Post by cneil on 2006-12-20
I'm using a bash shell in a gnome terminal.  I am trying to start a little bit of C programming.  I can't seem to get the british pound symbols and japanese yen symbols to output correctly.  

Here is the code that I am working with

#include <stdio.h>

[COLOR="Red"]#define POUNDS 0x9c[/COLOR]
[COLOR="Red"]#define YEN 0x9e[/COLOR]

int main()
{
        float amount,bp,jy;
        float d2p = 0.5407;     /*dollars per pound*/
        float d2y = 107.79;     /*dollars per yen*/

        printf("Enter the amount in dollars: $");
        scanf("%f", &amount);
        bp = amount * d2p;
        jy = amount * d2y;
        puts("Currency Conversion:");
        [COLOR="Red"]printf("%c%f\n",POUNDS,bp);[/COLOR]
        [COLOR="Red"]printf("%c%f\n",YEN,jy);[/COLOR]
        return(0);
}

---

### Post by mordox on 2006-12-20
The ASCII charset defines characters from 0 - 127 . The characters after that are dependent on the codepage you are using . When you will run the above program with codepage set IBM850 you can see a pound sign appearing in the gnome-terminal window. Don't use the ASCII values above 127. In the attached image you can see that.

---

### Post by steve.horsley on 2006-12-22
It's worse than that. I don't know about yen, but in ASCII, the UK pound sign is a national variant option that may be displayed differently by different display terminals.

However, I believe that gnome-terminal displays unicode. The unicode values are 0xa3 and 0xa5. Of course, any code you write that assumes gnome-terminal and used those values won't display right to other terminals such as ASCII ones.

---

