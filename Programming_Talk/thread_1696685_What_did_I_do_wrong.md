---
title: "What did I do wrong?"
date: 2011-02-27
forum: Programming Talk
---

### Post by KingOfHeart on 2011-02-27
[PHP]function HTMLToBBCode($message) 
{ 
    $html = array( 
    '/\<span class="ozentity">/'         => "[color=#E25500]", 
    '/\<span class="ozkey">/'         => "[color=#0000FF]",  
    '/\<span class="ozquote">/'         => "[color=#303030]",     
    '/\</span>/'         => "[/color]", 
    ); 
    $message = preg_replace(array_keys($html), array_values($html), $message);//line 27 
    return $message; 
} [/PHP][COLOR=#000000][COLOR=#007700]

got an error for line 27
[/COLOR][/COLOR]

---

### Post by foxmuldr on 2011-03-02
> **KingOfHeart said:**
> [PHP]function HTMLToBBCode($message) 
{ 
    $html = array( 
    '/\<span class="ozentity">/'         => "[color=#E25500]", 
    '/\<span class="ozkey">/'         => "[color=#0000FF]",  
    '/\<span class="ozquote">/'         => "[color=#303030]",     
    '/\</span>/'         => "[/color]", 
    ); 
    $message = preg_replace(array_keys($html), array_values($html), $message);//line 27 
    return $message; 
} [/PHP][COLOR=#000000][COLOR=#007700]

got an error for line 27
[/COLOR][/COLOR]

Is it the spurious trailing comma on line 25?

- Rick C. Hodgin

---

