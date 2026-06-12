---
title: "[SOLVED] GTK beginners question - overwriting in a text view"
date: 2008-05-02
forum: Programming Talk
---

### Post by anewguy on 2008-05-02
I have gotten some great help here getting to at least having a functional program, but need a little more help yet.  I have a text view which I write one line at a time to with newlines, so I guess in this case they are called paragraphs.  On some of the lines, I need to be able to "overwrite" them with the next line, but leave the preceeding buffer alone.  Is there a way to back up to start of paragraph?

Thanks in advance!!:)

EDIT:  Forgot to include, here's the test code I'm trying.  I'm trying to backspace over the text I've written after 9 lines (actually paragraphs in a text view since they each had a newline at the end) and just keep writing over the same line/paragraph.  The result of this code is no backspacing - just appending data to the line.  I thought that iter was supposed to be automatically reset when you do the call for backspace, so I have to assume that being so darn rusty in C that I'm doing something extremely stupid!!

:)
    int charcount =0;
      .
      . Beginning of a processing loop here
      .
      .  other stuff happens here but no gtk calls and nothing affecting
      .  linenum, iter, texttoshow or charcount
      .
      .
    sprintf(texttoshow,"At download: %d", linenum++);
     if (linenum <10)
      {
         strcat(texttoshow, "\n");
      }
    else
      {
        while (charcount > 0)
          {
            gtk_text_buffer_backspace ( buffer,
                                        &iter,
                                        FALSE,
                                        FALSE);
            charcount--;
          }
*
*
*  solved by adding the below to actually ERASE the buffer to end
*
*
        gtk_text_buffer_get_end_iter(buffer, &iter_end );
        gtk_text_buffer_delete(buffer, &iter,&iter_end );
        charcount = strlen(texttoshow);

*
* end of changes to make it work
*

        charcount = strlen(texttoshow);
      }
        
    gtk_text_buffer_insert(buffer, &iter, texttoshow , -1);

              .
              . end of a processing loop here
              .

---

### Post by anewguy on 2008-05-03
Unless you see something obviously wrong above, please ignor for now.  It just dawned on me in my testing that I only go through this entire routine 1 time for each button press, so the charcount is always 0 at the start.  I need to incorporate a loop in the testing so that it really duplicates what I need to do real-world.

Sorry!!

---

