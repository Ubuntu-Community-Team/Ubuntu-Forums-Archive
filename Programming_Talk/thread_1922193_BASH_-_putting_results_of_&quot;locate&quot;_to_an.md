---
title: "BASH - putting results of &quot;locate&quot; to an array"
date: 2012-02-08
forum: Programming Talk
---

### Post by sonicb00m on 2012-02-08
I would like to use the locate command to find a bunch of files and then iterate through the results to remove them.

Initially I used the find command but it's too slow

```

find / -name "fglrx" -exec rm -rf {} \;

```

So my idea was to place the results of locate into an array and then iterate the array and remove the found file.

Can anyone show me how to do this or even give me a more optimal solution?
Thanks

---

### Post by sudodus on 2012-02-08
This is a dangerous command! At least you should run it with echo inserted at first to make sure it does not delete too much.
```
find / -name "fglrx" -exec [COLOR="Red"]echo[/COLOR] rm -rf {} \;
```

---

### Post by sisco311 on 2012-02-08
There is no need for an array. You can pipe the output of locate to xargs:

```

# create a local database
updatedb -l 0 -o ~/my-db -U /path/to/dir
# delete files matched by PATTERN
locate --null -d ~/my-db PATTERN | xargs --null <the remove command here :)>
```

---

### Post by sonicb00m on 2012-02-09
Thanks a lot!

---

