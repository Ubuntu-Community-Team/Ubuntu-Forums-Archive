---
title: "SDL_RenderText"
date: 2009-07-03
forum: Programming Talk
---

### Post by hayden92 on 2009-07-03
Hey guys,

I'm having some difficulty at the moment with a program I'm writing. Basically, what the function in question needs to do is read from a text file, and the use "SDL_RenderText_Solid" to draw it up on the screen.

I don't really know how to do it, I thought of doing this:
```

char ch; // Make a char that reads individual characters

while(!file.eof())
{
    file.get(ch);

    // Convert them into an SDL text string...
    if (ch == '#') ttf_character = TTF_RenderText_Solid(font_small, "#", textColour);
    if (ch == '$') ttf_character = TTF_RenderText_Solid(font_small, "$", textColour);
    if (ch == '%') ttf_character = TTF_RenderText_Solid(font_small, "%", textColour);
    and so on
}

```
Obviously this would take a long time, and would also be inefficient (seeing as though I'd have to provide a definition for every ASCII character!

I did try this:
```

TTF_RenderText_Solid(font_small, 'ch', textColour);

```

But it results in the error "invalid conversion from ‘char’ to ‘const char*’"

Any help would be appreciated, because my hair is starting to fall out!

Thanks, Hayden

---

### Post by hayden92 on 2009-07-03
I just thought I should ask while I remember... it would be better if I could read an entire line using something like "file.getline(line, 512);" or something along those lines. 

Is there any way to read a line of text and convert it into an SDL_TTF surface?

---

