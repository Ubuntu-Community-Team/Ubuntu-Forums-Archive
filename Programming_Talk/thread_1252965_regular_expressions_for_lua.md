---
title: "regular expressions for lua"
date: 2009-08-29
forum: Programming Talk
---

### Post by manualqr on 2009-08-29
I'm using Lua as a scripting language in one of my projects, and I decided I wanted regex support. I took a good look at lrexlib, but I decided against it.

Now, I'm not trying to persuade you that lrexlib isn't worth using. It's actually much, *much* better than my solution. My only issue with lrexlib is that it's very large compared to the other components in my project.

This is for anyone that has the same issue with lrexlib;
```

#include <regex.h>
#include <stdbool.h>

static int lua_regex_match(lua_State* state) {
    if (lua_gettop(state) != 2) {
        return luaL_error(state, "bad args: #1: regex, #2: text");
    }
    
    const char* regex = luaL_checklstring(state, 1, NULL);
    const char* text = luaL_checklstring(state, 2, NULL);

    static regex_t rx;
    static int err;
 
    if ((err = regcomp(&rx, regex, 0)) != 0) {
        fprintf(stderr, "regcomp: %d\n", err);
        exit(err);
        // fail("lua_regex_match - could not compile regex");
    }
    
    lua_pushboolean(state,
        (regexec(&rx, text, 0, NULL, 0) == 0) ? true : false);    
    regfree(&rx);
        
    return 1;
}

// be sure to add register the function;
lua_register(state, "regex_match", lua_regex_match);

```

It's really simplistic, but it works;
```

-- will display "it works"
if regex_match(".*\\.c$", "lua_regex.c") then
  print("it works")
end

```

---

