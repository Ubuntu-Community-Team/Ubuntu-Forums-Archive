---
title: "[C] Malloc returning NULL"
date: 2012-11-03
forum: Programming Talk
---

### Post by Odexios on 2012-11-03
Hello everyone!

I'm having a weird issue with malloc.

I am using this code to allocate a matrix:

[php]static int grid_maze_create_matrix(void)
{
  int dim;
  int i;

  dim = grid_get_dim() / 2;

  maze_matrix = malloc(sizeof(int *) * dim);
  if (maze_matrix == NULL)
  {
    set_error(OOM);
    return ERROR;
  }
  
  for (i = 0; i < dim; i ++)
  {
    maze_matrix[i] = malloc(sizeof(int) * dim);
    if (maze_matrix[i] == NULL)
    {
      set_error(OOM);
      return ERROR;
    }
  }

  return OK;

}[/php]

maze_matrix is a global variable (I'm using it for debugging purposes) defined and initialized like this:

[php]int **maze_matrix = NULL;[/php]

while grid_get_dim() is a function that right now returns the int constant 19.

For some reason I don't understand, at the first step of the for cycle, at this line

[php]    maze_matrix[i] = malloc(sizeof(int) * dim);[/php]

malloc returns NULL.

I'm pretty sure I'm not running out of memory; valgrind confirms that I only did 22 allocations before, for a total of 1 576 bytes.

Any idea about what is wrong? Am I doing something really stupid that I'm not seeing?

---

### Post by Bachstelze on 2012-11-03
Are you certain it is that particular malloc() that returns NULL? Because

```
  maze_matrix = malloc(sizeof(int *) * dim);
  if (maze_matrix[i] == NULL)
  {
    set_error(OOM);
    return ERROR;
  } 
```

should be
```
  maze_matrix = malloc(sizeof(int *) * dim);
  if (maze_matrix == NULL)
  {
    set_error(OOM);
    return ERROR;
  } 
```

Also what on Earth is set_error()?

---

### Post by Odexios on 2012-11-03
> **Bachstelze said:**
> Are you certain it is that particular malloc() that returns NULL? Because

```
  maze_matrix = malloc(sizeof(int *) * dim);
  if (maze_matrix[i] == NULL)
  {
    set_error(OOM);
    return ERROR;
  } 
```

should be
```
  maze_matrix = malloc(sizeof(int *) * dim);
  if (maze_matrix == NULL)
  {
    set_error(OOM);
    return ERROR;
  } 
```

Also what on Earth is set_error()?
Yep; the matrix[i] is a copy-paste error, it's right in the source code. Correcting it in the op right now.

[php]int set_error(int code);[/php] is a function I wrote for a really primitive way to handle errors. It just sets a few variables, nothing that could interfere with what malloc does.

---

### Post by Bachstelze on 2012-11-03
> **Odexios said:**
> 
[php]int set_error(int code);[/php] is a function I wrote for a really primitive way to handle errors. It just sets a few variables, nothing that could interfere with what malloc does.

Regardless of the problem at hand, it sounds like a bad thing to do...

Anyway, it seems to work fine here so you will have to provide more details (how do you know that malloc() returned NULL?), and preferably your entire code.

---

### Post by Odexios on 2012-11-03
> **Bachstelze said:**
> Regardless of the problem at hand, it sounds like a bad thing to do...Yep, I guess it probably is; I'm not familiar with error handling in C yet, it's only been a few months since I started to seriously study programming, but I wanted to try to write a project a little larger than what I did in the past.

I'm almost at the end, but I cut a few (well, a lot of) corners, one of which is the error handling part; I just have a function, set_error, which sets a code for what went wrong, and a function, get_error, which returns that code. As I said, pretty primitive.

> Anyway, it seems to work fine here so you will have to provide more details (how do you know that malloc() returned NULL?), and preferably your entire code.I used gdb to check where malloc returned NULL after seeing that the function returned the out of memory error.

The complete program is about 20k lines of code, the part I'm debugging is around 500 lines but needs another 2500 to run. I'll paste it on pastebin when I have access to all the code again.

Thanks for the attention, by the way; it's appreciated.

---

