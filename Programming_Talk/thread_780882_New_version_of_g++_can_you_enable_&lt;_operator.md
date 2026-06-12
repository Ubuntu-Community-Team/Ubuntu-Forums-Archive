---
title: "New version of g++: can you enable &lt;? operator?"
date: 2008-05-03
forum: Programming Talk
---

### Post by Fixman on 2008-05-03
I noted that in the new versions of g++, the deprecated operators <?, >?, <?= and >?= were removed. Is there any compiler flag to put them back?

---

### Post by amingv on 2008-05-03
Not that I know; but you can use std::min() and std::max():

[PHP]#include <algorithm>
#include <iostream>

int main(){
    
    std::cout << "Minimum = " << std::min(5, 12) <<'\n';
    std::cout << "Maximum = " << std::max(5, 12) <<'\n';
    
    return 0;
}

[/PHP]

---

### Post by Fixman on 2008-05-04
> **amingv said:**
> Not that I know; but you can use std::min() and std::max():

[PHP]#include <algorithm>
#include <iostream>

int main(){
    
    std::cout << "Minimum = " << std::min(5, 12) <<'\n';
    std::cout << "Maximum = " << std::max(5, 12) <<'\n';
    
    return 0;
}

[/PHP]

I know that, but its always good to use the >?= operator for using less space on DP like algorithm problems.

---

### Post by amingv on 2008-05-05
> **Fixman said:**
> I know that, but its always good to use the >?= operator for using less space on DP like algorithm problems.

Yes, true. But AFAIK it really can't be helped. There's a ? operator you can't overload, and won't allow this.

[PHP]#include <iostream>
#include <string>

int main(){
    int number;
    std::string message;
    
    std::cout << "Insert any number less than ten\n";
    std::cin >> number;
    std::cin.ignore();

    /*It works like this:
    variable = (condition) ? value_if_true : value_if_false;*/
    message = (number < 10) ? "It's less than ten\n" : "It's not less than ten\n";
    
    std::cout << message;
    
    return 0;
    
    /*Notice that I type the condition with spaces for clarity; but it would be legal
    to write message=(number<10)?"It's less than ten\n":"It's not less than ten\n";
    that's why a confection such as <? cannot be allowed.
    You cannot overload this operator either, so there's not much choice left.
    
    One has to admit, though, that it's shorter than writing
    
    if (number < 10) {
        message = "It's less than ten\n";
    }
    else {
        message = "It's not less than ten\n";
    }
    */
}

[/PHP]

EDIT: Is something wrong with the PHP tags?

---

### Post by mssever on 2008-05-05
> **amingv said:**
> EDIT: Is something wrong with the PHP tags?
No, the forum software just saw <? and interpreted it as the start of a PHP script. That's the correct behavior, really.

---

### Post by amingv on 2008-05-05
> **mssever said:**
> No, the forum software just saw <? and interpreted it as the start of a PHP script. That's the correct behavior, really.

Yes that's what I assumed. I don't really know PHP so I don't know if it can be helped (maybe sanitize the string?).
Already made a report anyway:
[http://ubuntuforums.org/showthread.php?t=782517](http://ubuntuforums.org/showthread.php?t=782517)

---

### Post by LaRoza on 2008-05-05
> **amingv said:**
> Yes that's what I assumed. I don't really know PHP so I don't know if it can be helped (maybe sanitize the string?).
Already made a report anyway:
[http://ubuntuforums.org/showthread.php?t=782517](http://ubuntuforums.org/showthread.php?t=782517)

In PHP, the <? ?> tags or the <?php ?> tags must surround the code. Anything outside of them is just echo'd.

This allows PHP to be mixed with other markup easily (it also makes it very messy if one mixes them)

The sticky has a link to a "Scripting languages" guide, php is one of them.

---

