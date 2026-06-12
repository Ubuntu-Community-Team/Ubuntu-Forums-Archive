---
title: "Creating an array of pipes."
date: 2010-08-30
forum: Programming Talk
---

### Post by arkashkin on 2010-08-30
Hi,
I have a specific number of processes, which were created using fork(), those processes should communicate each with other using pipes. I want to create a dynamic array of pipes or use a Vector so it would contain all the pipes there were created.

each pipe should be of size of 2 integers so the array of the vector size should be arr[N][2].

my problem is that I don't know how to create properly this Vector or Array and pass it correctly to the dup2 function.

Maybe some one could help me with an example?

I build those two functions:

```
int** createArrOfPipes(int amount)
{
    int** arr = new int*[amount];

    for (int i=0;i<amount;i++)
    {
        arr[i] = new int[2];
    }

    return arr;
}

void freeArrOfPipes(int** arr, int amount)
{
    for (int i=0;i<amount;i++)
    {
        delete[] arr[i];
    }
    delete[] arr;
}

```

and tried to use vector, like this:

vector< vector<int> > pipes;
vector<int> read_vec1;
vector<int> write_vec2;
pipes.push_back(read_vec1);
pipes.push_back(write_vec2);


_but how to do some thing like this:_

```
       for(int i=0;i<(sub_commands.size()-1);i++)
        {
            pipe(**pipes[i]**);
        }

```

_or this:_

              ```
while (dup2 (**pipes[(command_index-1)][read]**, STDIN_FILENO) < 0)   //dup client's sock with stdin
                {
                    if (errno == EINTR) continue;

                    fprintf(stderr,"dup2 failed.");
                }
```

---

### Post by dwhitney67 on 2010-08-30
Consider something like:
```

#include <vector>

const size_t N = 32;

struct Pipes
{
   int rdwr[2];   // 0 = read, 1 = write
};

std::vector<Pipes> vec(N);

```
where N is the number of processes that you expect to fork.

Then after inserting items into the vector, you can use them as appropriate, within the dup2() call:
```

dup2(vec[0].rdwr[0], STDIN_FILENO);

```

---

