---
title: "Segmentation Fault outside loop"
date: 2015-08-31
forum: Programming Talk
---

### Post by Mohamed_Saad on 2015-08-31
Using C on Linux, I'm writing a code that stores all the information about the files in a directory using function stat() and prints them on the Terminal
The algorithm is quite simple, I made a structure array of "files" and dynamically allocated them. The structure contains a char array (string) so I dynamically allocated it too.
The thing is .. the dynamic allocation works fine but if I'm inside the while loop I can access the other element inside the structure - which is a structure stat object - but if I access it after the loop finishes, it gives me "Segmentation Fault"!
Here's the code

```

    #include <string.h>
    #include <stdio.h>
    #include <stdlib.h>
    #include <sys/types.h>
    #include <sys/stat.h>
    #include <unistd.h>
    #include <time.h>
    #include <pwd.h>
    #include <grp.h>
    #include <dirent.h>
    struct file{
        char* name;
        struct stat fbuf;
    };

            
    int main(int argc, char **argv)
    {
       char* dir=NULL;
       int k;
       dir=(char *)malloc(strlen(argv[argc-1])+1);
       strcpy(dir,argv[argc-1]);
       DIR *curr_dir;
       struct dirent *dir_inode;
       int i,j=0;
       char* sum=NULL;
       struct file* files=NULL;
       if ((curr_dir = opendir(dir)) == NULL) {
        fprintf(stderr, "Can't  Open %s\n", argv[1]);
        exit(2);
       }
        while (((dir_inode = readdir(curr_dir))) != NULL) {


        files=(struct file*) realloc(files,((j)+1)*(sizeof(char*)+sizeof(struct stat))); // Structure array reallocation	

        (files+(j))->name=(char *)(malloc(strlen(dir_inode->d_name)+1));//name allocation
                               
        
        
        for(i=0;i<strlen(dir_inode->d_name);i++)
            (files+(j))->name[i]=dir_inode->d_name[i];//name storage
        (files+(j))->name[i]='\0';

        sum= (char *) malloc(strlen(dir)+strlen(dir_inode->d_name)+2);//To add file name to its directory
                                
        for(i=0;i<strlen(dir);i++)
            sum[i]=dir[i];
        
        sum[i]='/';
        i++;
        for(k=0;dir_inode->d_name[k]!='\0';k++)
            sum[i+k]=dir_inode->d_name[k];
        sum[i+k]='\0';//file name with directory in sum
        
                                
        if( stat(sum,&((files+j)->fbuf)) == -1){ // the function gets information from the file name and stores them in fbuf
            printf("error stat\n");
            exit(1);
        }
        
        
        free(sum);
                if(    S_ISDIR(  (  (files+(j))->fbuf  ).st_mode  )    ){
                 printf("d");
                }
                else {
                   printf("-");
                }
    //Here the output appears fine
    //The output depends on accessing fbuf in files array
                                printf("statOK\n");
        (j)++; // index
        } 
                                printf("%d %d %d\n",files,j,files+1);



                                printf("%d\n",j);





       printf("\n\n\n\n");
       for(i=0;i<j;i++){
          printf("%s\n",(files+i)->name);
          printf("%d\n",files);
        //Starting from here, same syntax but outside the loop it gives the error
          if(    S_ISDIR(  (  (files+i)->fbuf  ).st_mode  )    ){
             printf("d");
          
          else {
             printf("-");
          }3
    }
    free(files);
    free(dir);
    closedir(curr_dir);
    exit(1);

    }

```
The code isn't complete yet but all what I want is to access the fbuf outside the loop, then I can complete it
Any ideas?

---

### Post by spjackson on 2015-09-01
> **Mohamed_Saad said:**
> 
```

        //Starting from here, same syntax but outside the loop it gives the error
          if(    S_ISDIR(  (  (files+i)->fbuf  ).st_mode  )    ){
             printf("d");
          
          else {
             printf("-");
          }3

```

I corrected the typos in the above code because it wouldn't compile.
```

        //Starting from here, same syntax but outside the loop it gives the error
          if(    S_ISDIR(  (  (files+i)->fbuf  ).st_mode  )    ){
             printf("d");
          }          
          else {
             printf("-");
          }

```
I cannot get the resulting code to produce a segmentation fault. Valgrind reports on some unfreed memory (because you don't free files[n].name) but doesn't report anything that would indicate memory trampling. If these corrections are the same as your original code before the posting errors, then I cannot think why you would be getting a segmentation fault. Perhaps you need to resort to gdb.

---

