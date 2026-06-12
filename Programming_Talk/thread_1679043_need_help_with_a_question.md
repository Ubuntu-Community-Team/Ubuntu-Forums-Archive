---
title: "need help with a question"
date: 2011-01-31
forum: Programming Talk
---

### Post by c2tarun on 2011-01-31
hi friends
I am trying to solve this problem:
[http://www.codechef.com/problems/COUNTREL/](http://www.codechef.com/problems/COUNTREL/)


here is my code:
```

#include<stdio.h>
#include<string.h>

int array[100],n;
int set[100];
int num=-1;
int sub[100][100];

void prnt(int n)
{
    int i;
    num++;
    for(i=1;i<=n;i++)
    {
        sub[num][i]=set[i];
//        printf("%d ",sub[num][i]);
    }
    printf("\n");
}

void subset(int e,int x,int count)
{
    int i;
    if(e>1)
    {
        for(i=x;i<=n-e+1;i++)
        {
            set[count]=array[i];
            subset(e-1,i+1,count+1);
        }
    }
    else
    {
        for(i=x;i<=n;i++)
        {
            set[count]=array[i];
            prnt(count);
        }
    }
}

int compare(int i,int j)
{
    int cnt=1;
    int chk=1;
    while(sub[i][cnt]!=0)
    {
        chk=1;
        while(sub[j][chk]!=0)
        {
        if(sub[i][cnt]==sub[j][cnt])
            return 1;
        chk++;
        }
        cnt++;
    }
    return 0;
}

int main()
{
    int t;
    int R1,R2;
    scanf("%d",&t);
    while(t--)
    {
        R1=R2=0;
        memset(sub,0,sizeof(sub));
        scanf("%d",&n);
        int i,j;
        for(i=1;i<=n;i++)
            array[i]=i;
        for(i=1;i<=n;i++)
        {
            subset(i,1,1);
        }

        for(i=0;i<=num;i++)
        {
            j=1;
            while(sub[i][j]!=0)
                printf("%d ",sub[i][j++]);
            printf("\n");
        }


        for(i=0;i<=num;i++)
            for(j=i+1;j<=num;j++)
            {
                if(compare(i,j))
                    R1++;
                else
                    R2++;
            }

        printf("%d %d\n",R1,R2);
    }

}

```

I am getting the wrong output.
They provided the solution in editorial.
here is what the said about the solution:


> 

 Part 1 closed form: (3^n+1)/2 - 2^n
Part 2 closed form: 2*4^(n-1) - 3^n + 2^(n-1) + 2^n - (3^n+1)/2 
           The answer (for both 1 and 2) is in the form of a*4^n + b*3^n + c*2^n + d for some small constants a,b,c,d.
You can calculate 4^n%MOD, 3^n%MOD, 2^n%MOD in log(n) time using fast exponentiation for an overall complexity of O(log(n)).
 


I am not able to understand their solution, and my program is giving me wrong output.
Can anyone please help.

---

### Post by Tony Flury on 2011-02-01
i can't help with your problem, number theorem is not my forte - but you might find that being more specific in your Title might help you get the answers that you need - after all nearly everyone who posts to these forums "need(s) help with a question".

---

### Post by c2tarun on 2011-02-01
> **Tony Flury said:**
> i can't help with your problem, number theorem is not my forte - but you might find that being more specific in your Title might help you get the answers that you need - after all nearly everyone who posts to these forums "need(s) help with a question".

very sorry :)
how can i change the subject?

---

### Post by Tony Flury on 2011-02-01
Not sure you can on an open thread - you might be able to get an Admin to do it by using the report button - and suggesting a new thread title. It was more of a "helpful hint" for the future.

---

