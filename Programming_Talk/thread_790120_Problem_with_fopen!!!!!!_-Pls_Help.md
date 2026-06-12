---
title: "Problem with fopen!!!!!! -Pls Help"
date: 2008-05-11
forum: Programming Talk
---

### Post by murali_dilemma_fopen on 2008-05-11
Greetings UBUNTU users,

     Need help from you folks big time.Tis about fopen command in C.As we all know fopen takes the name of the file and permissions as its arguments.But in my application I would need to take the name of the file from the user.Easy as it may seem, I have been running into troubles with this concept.The fopen doesnt seem to be taking well to the file name stored in a variable and fed into it.My entire software is stuck becos of this.I am attaching my code herewith for you kind folks to have a look.

#include "stdio.h"
int main()
{
	FILE *stream;
         int i;
	char filename[20];

    
    printf("Enter filename \n");
	for(i=0;i<12;i++)
	{
		scanf("%c",&filename[i]);
	}

	for(i=0;i<12;i++)
	{
		printf("%c",filename[i]);
	}

	if( (stream = fopen( "filename", "rb" )) != NULL )
	{
	  printf("Successful\n");
	}

	else
	{ 

		printf("Not Successful\n");
		printf("%d \n",stream);
	}
}



 ..........I t seems to be printing **"not succesful"** all the time.I request all you wise folks to help me out on this regard and kindly do send your answers to **amuralikrishnan@hdmedicalgroup.com**      ASAP.


    And oh yeah by the way the one with this format of scanf...

 printf("Enter filename \n");
    scanf("%s",filename);

           Evn this does not work.So plllllz help me out.

              Murali

---

### Post by KIAaze on 2008-05-11
You made a mistake here:
```
if( (stream = fopen( "filename", "rb" )) != NULL )

```
It should be:
```
if( (stream = fopen( filename, "rb" )) != NULL )

```

Working code:

```
#include "stdio.h"
int main()
{
FILE *stream;
int i;
char filename[20];


printf("Enter filename \n");
scanf("%s",&filename);
printf("%s\n",filename);
// for(i=0;i<12;i++)
// {
// scanf("%c",&filename[i]);
// }
// 
// for(i=0;i<12;i++)
// {
// printf("%c",filename[i]);
// }

if( (stream = fopen( filename, "rb" )) != NULL )
{
printf("Successful\n");
}

else
{

printf("Not Successful\n");
printf("%d \n",stream);
}
}

```

I tried keeping the scanf("%c"), but it didn't work.
And scanf("%s") is just easier and works here.
I suppose it has something to do with the terminating \0 or \n.

---

