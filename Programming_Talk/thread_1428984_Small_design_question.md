---
title: "Small design question"
date: 2010-03-13
forum: Programming Talk
---

### Post by hanniph on 2010-03-13
Hey,

Which way is better?

```

@user.register_word(Word.new(param1, param2 etc))

# -- 
def register_word(word)
  words.append(word)
end


```

or 

```

@user.register_word(param1, param2 etc)

# --
def register_word(param1, param2 etc)
  words.append(Word.new(param1, param2 etc))
end

```

Which way do you prefer (cleaner, looks better or anything)? I cannot decide :(

---

### Post by era86 on 2010-03-13
First one makes more sense to me.

---

### Post by km0r3 on 2010-03-13
First one.

**Explicit is better than implicit.**

---

### Post by hanniph on 2010-03-13
Yeah, and if suddenly I realized that I need to change the way Word objects are constructed, I would need to change the code only in one place.

---

