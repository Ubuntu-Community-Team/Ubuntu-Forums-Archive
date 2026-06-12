---
title: "Python Syntax Help!"
date: 2011-12-05
forum: Programming Talk
---

### Post by rohan1413 on 2011-12-05
```

def parse_actor_data(actor_data):
    ##creating a list of words from the relevant lines from the open text file. it goes through the first fourteen lines and then stops to the line of 77 hashes and stores all the other lines
    actor_file = actor_data
    line_number = 0
    list_of_lines = []
    end_loop = True
    while end_loop:
        if line_number < 14:
            line_number += 1
        elif line.startswith("-----------------------------------------------------------------------------"):
            end_loop = False
        else:
            list_of_lines.append(line.split()
    ##ABCABC
    line_number = 0
    final_dictionary = {}
    last_actor = ""
    while line_number < len(list_of_lines):
        movie_name = ""
        index_of_line = line_number
        words_in_previous_line = list_of_lines[line_number - 1].split()
        words_in_this_line = list_of_lines[line_number].split()
        ##getting the actor name, if the line has it, by analyzing if there is a part of the line with a comma
        if(line_number == 0 or (len(words_in_previous_line) == 0)):
            index_of_comma = find_index_with_string(words_in_this_line, ",")
            actor_lastname = words_in_this_line[index_of_comma].strip(",")
            index_1 = index_of_comma - 1
            while index_1 >= 0:
                actor_lastname = words_in_this_line[index_1] + " " + actor_lastname
                index_1 -= 1
            actor_firstname = words_in_this_line[index_of_comma + 1]
            actor_name = actor_firstname + " " + actor_lastname
            last_actor = actor_name
            final_dictionary[actor_name] = []
            ##adding in the movie
            index_of_bracket = find_index_with_string(words_in_this_line, ")")
            index_1 = index_of_comma + 2
            while index_1 <= index_of_bracket:
                movie_name = movie_name + " " + words_in_this_line[index_1]
                index_1 += 1
            final_dictionary[last_actor].append(movie_name)    
        ##if the line does not contain an actor    
        else:      
            index_of_bracket = find_index_with_string(words_in_this_line, ")")
            index_1 = 0
            while index_1 <= index_of_bracket:
                movie_name = movie_name + " " + words_in_this_line[index_1]
                index_1 += 1
            final_dictionary[last_actor].append(movie_name) 
        line_number += 1
    return final_dictionary

```I always get a syntax error after the ##ABCABC comment - I have no idea why. I don't think I've done anything wrong in terms of program logic - I thought it might be reusing the variable "line_number" but apparently that's okay. 

Any ideas guys? Thanks!

---

### Post by lykwydchykyn on 2011-12-05
Can you put your code in code tags?  Python without whitespace is pretty much indecipherable.

---

### Post by CoffeeRain on 2011-12-05
Usually when I have weird errors in python code, I find it is because of a missing paren or quote, but like he said, it's hard to read without being wrapped in the code tags.

---

### Post by Bodsda on 2011-12-05
as others have said, if the code isnt in code tags we cant see whats going wrong. The traceback would also be useful.

---

### Post by rohan1413 on 2011-12-05
Noted, didn't realize that after I repasted the code it deleted the indents again.

Pretty new to posting on forums lol

---

### Post by drmrgd on 2011-12-05
It also might be helpful to see the actual error that Python is throwing.  It could at least help us know where to look.

---

### Post by rohan1413 on 2011-12-05
The actual error I get is this, taken straight from the python shell

>>> [evaluate functions.py]
Traceback (most recent call last):
  File "/Users/Rohan/functions.py", line 15, in <module>
invalid syntax: /Users/Rohan/functions.py, line 15, pos 15

---

### Post by 11jmb on 2011-12-05
You're missing a close-paren above #ABCABC (line 13)

---

### Post by rohan1413 on 2011-12-05
Thank you so much!

Three hours down the drain for nothing lol.

---

### Post by lykwydchykyn on 2011-12-05
After many years of coding I've learned that the longer you spend hunting down a bug, the simpler the bug is likely to be.

3 hours sounds about right for a missing parenthesis. :)

---

### Post by CoffeeRain on 2011-12-05
Yeah, after many times with this happening to me, I have found out that when a syntax error shows up and just points randomly to the middle of a word, it's probably a missing paren.

---

### Post by StephenF on 2011-12-06
> **lykwydchykyn said:**
> After many years of coding I've learned that the longer you spend hunting down a bug, the simpler the bug is likely to be.

3 hours sounds about right for a missing parenthesis. :)
How about a year to discover that the comments don't run.

set thread control variable
# waiting for the worker thread to stop
clean up

This one would cause random memory corruption.
:lolflag:

---

