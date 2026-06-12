---
title: "C: writing to binary file (and reading)?"
date: 2007-10-31
forum: Programming Talk
---

### Post by happogiri on 2007-10-31
Once again I'm knee deep in...something.

I'm sorry for the not-so-illustrating translations of my variables and such.
```

/* For example: "Wheatflour    3 cups" */
typedef struct ingredient {
   char *name;
   int nSize;   /* Length of name */
   float amount; 
   char *unit;
   int uSize; /* Length of unit */
} Ingredient;

typedef struct recipe {
   char *name; /* For example "Pizza Bolognese" */
   int nSize;
   Ingredient **ingredients;
   int iAmount; /* How many ingredients */
   char *howto; /* Howto cook */
   int hSize; /* Length of howto */
} Recipe;

typedef struct list {
   Recipe *recipe; 
   struct list *next; 
} Cookbook;

```

Here are my three structures. This is supposed to be a cookbook, collection of recipes. Everytime the program starts it reads the recipes from binary file to linked list and when it shuts it writes them to file (you can browse, add, remove, edit, etc...). Anyways, my problem is that I can't figure it out how to write and read that certain float-amount in Integer to (and from) binary file. 

Here is how I write them in file:
```

void writeRecipesToFile(char *fname, Cookbook *head) {
    FILE *tmpFile;
   Cookbook *tmp;
   int strSize;
   int i;
   tmp = head;

   if((tmpFile = fopen(fname, "wb")) == NULL) {
       printf("Error...!");
       exit(EXIT_FAILURE);
   }
   while(tmp != NULL) {
       fwrite(&(tmp->recipe->nSize), sizeof(int), 1, tmpFile);
       fwrite(tmp->recipe->name, tmp->recipe->nSize, 1, tmpFile);
       fwrite(&(tmp->recipe->iAmount), sizeof(int), 1, tmpFile);
       for(i = 0; i < tmp->recipe->iAmount; i++) {
            fwrite(&(tmp->recipe->ingredients[i]->nSize), sizeof(int), 1, tmpFile);
            fwrite(tmp->recipe->ingredients[i]->name, tmp->recipe->ingredients[i]->nSize, 1, tmpFile);
            fwrite(&(tmp->recipe->ingredients[i]->amount), sizeof(float), 1, tmpFile);
            fwrite(&(tmp->recipe->ingredients[i]->uSize), sizeof(int), 1, tmpFile);
            fwrite(tmp->recipe->ingredients[i]->unit, tmp->recipe->ingredients[i]->uSize, 1, tmpFile);
       }
       fwrite(&(tmp->recipe->hSize), sizeof(int), 1, tmpFile);
       fwrite(tmp->recipe->howto, tmp->recipe->hSize, 1, tmpFile);
      
       tmp = tmp->next;

   }
   fclose(tmpFile);
}


```

Is there any sense in it? 
The reading is kind of similar but with fread(). 
```

void readRecipesFromFile(char *fname, Cookbook **head) {
    FILE *tmpFile;

    Recipe *tmpRecipe;
    char *rname, *rhowto;
    int rnSize, rhSize;
    int iam;

    Ingredient **tmpIng;
    char *iname, *iunit;
    int inSize, iuSize;
    float amount;

    int i;

    if((tmpFile = fopen(fname, "rb")) == NULL) {
        printf("Error!");
        exit(EXIT_FAILURE);
    }
LOOP UNTIL END OF FILE {
        fread(&rnSize, sizeof(int), 1, tmpFile);
        if((rname = malloc(rnSize)) == NULL) {
            exit(EXIT_FAILURE);
        }
        fread(rname, rnSize, 1, tmpFile);
        fread(&iam, sizeof(int), 1, tmpFile);

        for(i = 0; i < iam; i++) {
            fread(&inSize, sizeof(int), 1, tmpFile);
            if((iname = malloc(rnSize)) == NULL) {
                exit(EXIT_FAILURE);
            }
            fread(iname, rnSize, 1, tmpFile);
            if(fread(&amount, sizeof(float), 1, tmpFile) != 1) { 
                printf("Error!");
                exit(EXIT_FAILURE);
            }
            fread(&iuSize, sizeof(int), 1, tmpFile);
            if((iunit = malloc(rnSize)) == NULL) {
                exit(EXIT_FAILURE);
            }
            fread(iunit, iuSize, 1, tmpFile);
        
            tmpIng[i] = createIngredient(iname, amount, iunit);
            free(iname);
            free(iunit);
        }

        fread(&rhSize, sizeof(int), 1, tmpFile);
        fread(rhowto, rhSize, 1, tmpFile);

        createRecipe(rname, rhowto, tmpIng, iam, &tmpRecipe);
        void addRecipeToList(head, tmpReciper);
        free(rname);
        free(rhowto);
} END LOOP   
   fclose(tmpFile);
}

```

The writing seems to work so and so, but when I print the values I've read, the "float amount" -value in Ingredient is something like: 686098745690300000.00000 and after that everything else is garbage too. When I write the file as normal text-file everything seems to be there (all the numbers, int and float, are "binary" but text is there). So, where did I go wrong (please, be gentle)?

I will check the return values of each function ( if(fread(....) != 1) dosomething...) when I know I can make it work. :)

---

### Post by Bliepo32 on 2007-10-31
nevermind this. Didn't read your post well and made a reply.

---

### Post by ilsd on 2007-10-31
first: read man intently!

you mix up arguments in fwrite() and fread() .
second argument is not a data length! it's number of elements you want to write/read. each element size is a 3d arg.
and i think it's simpler write/read whole structure at one fwrite/fread

correct:

fwrite(&val, 1, sizeof(val), f);

---

### Post by happogiri on 2007-10-31
^^ I think you can put them either way.  

size_t fwrite(const void *ptr, size_t size, size_t nmemb, FILE *stream);
Writes data from the array pointed to by ptr to the given stream. It writes nmemb number of elements of size size. The total number of bytes written is (size*nmemb).

I can't figure how I can write or read the whole structure. 

> fwrite(&val, 1, sizeof(val), f);

Isn't sizeof(MyStructure) in my case just about 20 -30 bytes because theres pointers (4 bytes each?) and few integers?

---

### Post by ilsd on 2007-10-31
> **happogiri said:**
> ^^ I think you can put them either way.  

size_t fwrite(const void *ptr, size_t size, size_t nmemb, FILE *stream);
Writes data from the array pointed to by ptr to the given stream. It writes nmemb number of elements of size size. The total number of bytes written is (size*nmemb).
i said so ;)

> **happogiri said:**
> 
I can't figure how I can write or read the whole structure. 

Isn't sizeof(MyStructure) in my case just about 20 -30 bytes because theres pointers (4 bytes each?) and few integers?

ok.. in special case where struct has no array pointers you can calculate size of data. peace?

---

### Post by happogiri on 2007-11-01
> **ilsd said:**
> i said so ;)



ok.. in special case where struct has no array pointers you can calculate size of data. peace?

Man, I'm not seeing it. Tell me, so I can be in peace! :)

---

### Post by YetAnotherNoob on 2007-11-01
I smell overdue homework.
:)

---

### Post by happogiri on 2007-11-01
> **YetAnotherNoob said:**
> I smell overdue homework.
:)

It's soon overdue if I can't figure this out! :)

---

### Post by dubemasterd88 on 2007-11-01
....

---

