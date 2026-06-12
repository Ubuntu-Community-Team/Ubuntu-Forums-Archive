---
title: "function to get the generation page time"
date: 2010-07-26
forum: Programming Talk
---

### Post by astkboy2008 on 2010-07-26
today i got very nice php function from jooria
its give you the generation page time
the function:[PHP]function gen_time() {
    static $time;
        if($time== 0){
            $time= microtime(true);
        }else{
            return (string)(microtime(true)-$time);
        }
}[/PHP]
how you can use:[PHP]gentime();

# your source code here

echo 'Generated in '.gentime().' seconds.'[/PHP]
[the snippet]("http://www.jooria.com/snippets?snippet=114")

---

