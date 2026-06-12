---
title: "iterating along a string, stopping at the end? help!"
date: 2006-12-07
forum: Programming Talk
---

### Post by Choad on 2006-12-07
```

std::getline(levelData, line);
for (i = 0; (line[i] != NULL); i++)
{

}

```

now that doesnt work, but you can see what i was trying to say. how can i stop the for loop when the characters in line[] run out?

---

### Post by tribaal on 2006-12-07
You might want to test for '\0' and/or '\n' instead of NULL. In C there is no restriction to read after an array's upper bound, you'll just keep reading random memory chuncks...

Hope I make sense :)

- trib'

---

### Post by Choad on 2006-12-07
> **tribaal said:**
> You might want to test for '\0' and/or '\n' instead of NULL. In C there is no restriction to read after an array's upper bound, you'll just keep reading random memory chuncks...

Hope I make sense :)

- trib'
'\0' works a charm

thanks!

---

