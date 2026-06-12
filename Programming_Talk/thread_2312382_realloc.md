---
title: "realloc"
date: 2016-02-04
forum: Programming Talk
---

### Post by chuchi on 2016-02-04
Hi there!

I have seen some examples of realloc. Most of them use two pointers, the first one to be passed as a parameter to realloc an the second one to save the return of realloc. Then the first pointer is assigned to the second pointer. Here is an example ([http://www.cplusplus.com/reference/cstdlib/realloc/](http://www.cplusplus.com/reference/cstdlib/realloc/))

```

int input, n;
int* numbers = NULL;
int* more_numbers = NULL;
do {
     printf ("Enter an integer value (0 to end): ");
     scanf ("%d", &input);
     count++;

     more_numbers = (int*) realloc (numbers, count * sizeof(int));

     if (more_numbers!=NULL) {
       numbers=more_numbers;
       numbers[count-1]=input;
     }
     else {
       free (numbers);
       puts ("Error (re)allocating memory");
       exit (1);
     }
  } while (input!=0);

```

My question: Is there any problem to use only one pointer?? This code works well for me:

```


int input, n;
    int count = 0;
    int* numbers = NULL;

    do
    {
        printf("Enter an integer value (0 to end): ");
        scanf("%d", &input);
        count++;

        numbers = (int*) realloc(numbers, count * sizeof (int));

        if (numbers != NULL)
        {
            numbers[count - 1] = input;
        }
        else
        {
            free(numbers);
            puts("Error (re)allocating memory");
            exit(1);
        }
    }
    while (input != 0);

```

Or is it considered a bad practice? 

Thank you very much in advance!

---

### Post by spjackson on 2016-02-04
The difference is what happens when realloc fails. In the original, free(numbers) releases the memory that was allocated earlier. In your second version, free(numbers) does nothing because numbers is NULL.

---

### Post by chuchi on 2016-02-04
Ok [**[COLOR=#000000]spjackson[/COLOR]**]("http://ubuntuforums.org/member.php?u=1128302") I see your point and I agree with you.

Thank you very much!

---

