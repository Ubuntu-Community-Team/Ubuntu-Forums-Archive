---
title: "des in c language, help needed"
date: 2009-02-25
forum: Programming Talk
---

### Post by AlexenderReez on 2009-02-25
[PHP]#include<string.h>
char ep[8],p10[10],p8[8],ip[8],ip1[8],pr[10],key1[8],key2[8],p4[4];
int s0[4][4]={{1,0,3,2},{3,2,1,0},{0,2,1,3},{3,1,3,2}}
,s1[4][4]={{0,1,2,3},{2,0,1,3},{3,0,1,0},{2,1,0,3}};
void p10f(char ab[10])
{
 strcpy(p10,"\0");
 p10[0]=ab[2];p10[1]=ab[4];p10[2]=ab[1];p10[3]=ab[6];p10[4]=ab[3];
 p10[5]=ab[9];p10[6]=ab[0];p10[7]=ab[8];p10[8]=ab[7];p10[9]=ab[5];
}
void p8f(char cd[10])
{
 strcpy(p8,"\0");
 p10[0]=cd[5];p10[1]=cd[2];p10[2]=cd[6];p10[3]=cd[3];p10[4]=cd[7];
 p10[5]=cd[4];p10[6]=cd[9];p10[7]=cd[8];
}
void p4f(char lm[4])
{
 strcpy(p4,"\0");
 p4[0]=lm[1];p4[1]=lm[3];p4[2]=lm[2];p4[3]=lm[0];
}

void epf(char ed[4])
{
 strcpy(ep,"\0");
 ep[0]=ed[3];ep[1]=ed[0];ep[2]=ed[1];ep[3]=ed[2];ep[4]=ed[1];
 ep[5]=ed[2];ep[6]=ed[3];ep[7]=ed[0];
}
void ipf(char ef[8])
{
 strcpy(ip,"\0");
 ip[0]=ef[1];ip[1]=ef[5];ip[2]=ef[2];ip[3]=ef[0];ip[4]=ef[3];
 ip[5]=ef[7];ip[6]=ef[4];ip[7]=ef[6];
}
void ip1f(char ef[8])
{
 strcpy(ip1,"\0");
 ip1[0]=ef[3];ip1[1]=ef[0];ip1[2]=ef[2];ip1[3]=ef[4];ip1[4]=ef[6];
 ip1[5]=ef[1];ip1[6]=ef[7];ip1[7]=ef[5];
}
const char* substr(char* pra,int strt,int end)
{
  int j,k=0;
  char *a;
  for(j=strt,k=0;j<=end&&k<=(end-strt);j++,k++)
    a[k]=pra[j];
  return a;
}
const char* leftshift(char* vam,int sid)
{
  int tmp;
  char* chaitu;
  for(tmp=0;tmp<strlen(vam);tmp++)
     chaitu[tmp]=vam[tmp]-sid;
  return chaitu;
}
const char* exor(char* pra,char* div)
{
  int x;
  char* out;
  for(x=0;x<strlen(pra);x++)
  {
    if(pra[x]==div[x])
     out[x]='0';
    else
     out[x]='1';
  }
  return out;
}
void genkey(char keyz[10])
{
 char pra[5],giri[5],raj[5],vasu[5],sri[10];
 strcpy(key1,"\0");
 strcpy(key2,"\0");
 strcpy(pra,substr(keyz,0,4));
 strcpy(giri,substr(keyz,5,9));
 strcpy(raj,leftshift(pra,1));
 strcpy(vasu,leftshift(giri,1));
 strcpy(sri,strcat(raj,vasu));
 p8f(sri);
 strcpy(key1,p8);
 strcpy(pra,substr(key1,0,4));
 strcpy(giri,substr(key1,5,9));
 strcpy(raj,leftshift(pra,2));
 strcpy(vasu,leftshift(giri,2));
 strcpy(sri,strcat(raj,vasu));
 p8f(sri);
 strcpy(key2,p8);
}
int toNumber(char re[2]){
int hi;
if(strcmp(re,"00")==0)
hi=0;
if(strcmp(re,"01")==0)
hi=1;
if(strcmp(re,"10")==0)
hi=2;
if(strcmp(re,"11")==0)
hi=4;
return hi;
}
const char* binary(int ki)
{
char trap[2];
  if(ki==0)
    strcpy(trap,"00");
  if(ki==1)
    strcpy(trap,"01");
  if(ki==2)
    strcpy(trap,"10");
  if(ki==3)
    strcpy(trap,"11");
  return trap;
}
int main()
{
char ptxt[8],key[10],temptxt[8],temptxt1[8],temp[4],
temp2[8],tmpx[2],tmpy[2],temp3[4],outsx,outsy,tmpu[2],
tmpv[2],templ[2],tempr[2],tempq[4],temp4[4],tempw[4],
tmptxt[8],tmpin[4];
int i,j,m,n;
clrscr();
printf("\t");
printf("Enter The Plain Txt of 8 bits");
scanf("%s",ptxt);
printf("Enter the Key(10 bits)");
scanf("%s",key);
genkey(key);
ipf(ptxt);
strcpy(temp,substr(ip,4,7));
strcpy(tempw,substr(ip,0,3));
epf(temp);
strcpy(temp2,exor(ep,key1));
strcpy(temp3,substr(ip,0,3));
strcpy(temp4,substr(ip,4,7));
tmpx[0]=temp3[0];tmpx[1]=temp3[3];
tmpy[0]=temp3[1];tmpy[1]=temp3[2];
i=toNumber(tmpx);j=toNumber(tmpy);
tmpu[0]=temp4[0];tmpu[1]=temp4[3];
tmpv[0]=temp4[1];tmpv[1]=temp4[2];
m=toNumber(tmpu);n=toNumber(tmpv);
strcpy(templ,binary(s1[i][j]));
strcpy(tempr,binary(s1[m][n]));
strcpy(tempq,"\0");
strcat(tempq,templ);
strcat(tempq,tempr);
p4f(tempq);
strcpy(tmpin,exor(p4,tempw));
strcpy(tmptxt,"\0");
strcat(tmptxt,temp);
strcat(tmptxt,tmpin);
strcpy(temp,substr(tmptxt,4,7));
strcpy(tempw,substr(tmptxt,0,3));
epf(temp);
strcpy(temp2,exor(ep,key2));
strcpy(temp3,substr(ip,0,3));
strcpy(temp4,substr(ip,4,7));
tmpx[0]=temp3[0];tmpx[1]=temp3[3];
tmpy[0]=temp3[1];tmpy[1]=temp3[2];
i=toNumber(tmpx);j=toNumber(tmpy);
tmpu[0]=temp4[0];tmpu[1]=temp4[3];
tmpv[0]=temp4[1];tmpv[1]=temp4[2];
m=toNumber(tmpu);n=toNumber(tmpv);
strcpy(templ,binary(s1[i][j]));
strcpy(tempr,binary(s1[m][n]));
strcpy(tempq,"\0");
strcat(tempq,templ);
strcat(tempq,tempr);
p4f(tempq);
strcpy(tmpin,exor(p4,tempw));
strcpy(tmptxt,"\0");
strcat(tmptxt,temp);
strcat(tmptxt,tmpin);
ip1f(tmptxt);
printf("%s",ip1);
return 0;
}[/PHP]

there are few problems within the code...any help is really appreciated!

---

### Post by jimi_hendrix on 2009-02-25
can you give us more info?

---

### Post by Can+~ on 2009-02-25
Scary piece of code, almost TDWTF worthy.

---

### Post by AlexenderReez on 2009-02-25
> **jimi_hendrix said:**
> can you give us more info?

[http://ubuntuforums.org/showthread.php?t=1080008](http://ubuntuforums.org/showthread.php?t=1080008)

i cant't able to use this code.so i need to create similar script that do same job... it is encryption and decryption using des algorithm . 

> **Can+~ said:**
> Scary piece of code, almost TDWTF worthy.



it is scary...as it is not weel organize the structure...but i believe people still can read it...i will reorganize it after it is working.



please help!

---

### Post by dwhitney67 on 2009-02-25
AlexenderReez

I played around with the code you posted today (and sometime ago in the past when I did IA work for the NSA), and I still have never been able to figure out how to use it.

The API for encrypting and decrypting is not described at all in the code you obtained, so just knowing what the parameter types are is not sufficient.  I know, because I created the 64-byte arrays, passed them to the encryption function, only to find that the function SegFaulted during runtime.

So if you can find some documentation for the code you presented, please post it.  Otherwise, consider the DES code you posted earlier today (see [here]("http://ubuntuforums.org/showpost.php?p=6795760&postcount=3")) to be dung.

---

### Post by AlexenderReez on 2009-02-25
> **dwhitney67 said:**
> AlexenderReez

I played around with the code you posted today (and sometime ago in the past when I did IA work for the NSA), and I still have never been able to figure out how to use it.

The API for encrypting and decrypting is not described at all in the code you obtained, so just knowing what the parameter types are is not sufficient.  I know, because I created the 64-byte arrays, passed them to the encryption function, only to find that the function SegFaulted during runtime.

So if you can find some documentation for the code you presented, please post it.  Otherwise, consider the DES code you posted earlier today (see [here]("http://ubuntuforums.org/showpost.php?p=6795760&postcount=3")) to be dung.

i prefer to use earlier code but it is not working..any help ofr that post is really appreciated!

---

### Post by dwhitney67 on 2009-02-25
> **AlexenderReez said:**
> i prefer to use earlier code but it is not working..any help ofr that post is really appreciated!
I agree, it would be nice.  But without documentation, or at a minimum, a working example, it would take more effort than I care to expend trying to figure out how to get it to work.

---

### Post by soltanis on 2009-02-25
This *is* C, right? Because the code tag seems to think it's PHP.

What is with all the strings being thrown around? Wouldn't it be easier (and less fault-prone) if you converted things to their actual binary representations and then manipulated them?

---

### Post by Tony Flury on 2009-02-26
[QUOTE=soltanis;6801356]This *is* C, right? Because the code tag seems to think it's PHP.
[QUOTE]

Ignore the fact that the tags say PHP - lots of people in these forums use the PHP tag rather than CODE tags to post source code, I am not sure why. It is enrirely personal choice, and does not actually mean that the quoted code is PHP.

---

### Post by Tony Flury on 2009-02-26
> **AlexenderReez said:**
> i prefer to use earlier code but it is not working..any help ofr that post is really appreciated!
Alexender : in your earlier thread a lot of people have tried to help you get your code to work - in that case it is not the code that does not work, but more about how you are trying to use it. I suggest you go back and read all of those comments again (in the previous thread - ignoring the one about using sudo).

---

