---
title: "Small curses program not displaying"
date: 2012-04-20
forum: Programming Talk
---

### Post by Alf Stockton on 2012-04-20
Please tell me what I have done wrong in the following code extract.
The mvwaddstr does not display even though I know I am getting characters from the keyboard.
InputString also apparently does not get populated? Help please. 
```

    while(1)
        {
        j = 0;
        while((i = wgetch(xwin)) != EOF)
            {
            if ((i == 0x51) || (i == 0x71) || (i == 0x1B)) break; // q or Q or ESC
            InputString[j++] = i;
            }

        if ((i == 0x51) || (i == 0x71) || (i == 0x1B)) break; // q or Q or ESC
        // check for carriage return/line feed & remove same
        if ((InputString[strlen(InputString)] == 0x0A) || (InputString[strlen(InputString)] == 0x0D))
            {
            strncpy(OutputString, InputString, strlen(InputString)-1);
            }
        else 
            {
            strcpy(OutputString, InputString);
            }

        Result = mvwaddstr(xwin, y, x, OutputString);
        if (Result != 0) waddch(xwin, Result);

//          while((i = wgetch(xwin)) != EOF) waddch(xwin, i);
        wmove(xwin, ++y, x);
        wrefresh(xwin);
        }

```

---

