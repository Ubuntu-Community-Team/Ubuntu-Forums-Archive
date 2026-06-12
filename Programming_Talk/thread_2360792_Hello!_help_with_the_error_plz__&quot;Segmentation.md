---
title: "Hello! help with the error plz : &quot;Segmentation fault (core dumped)&quot;"
date: 2017-05-08
forum: Programming Talk
---

### Post by noamisr6 on 2017-05-08
Hello dear, 
i'm trying to make solution to class , and i get this error "Segmentation fault (core dumped)".
i need to find a similar words.
i saw many posts about for this problem , but i didnt get why and how can i find the problem.
BTW i'm sorry if my post is not illgel i'm new here.
ty.
[PHP]
BT
void main()
{
  char DecipherText[D];
  char Words[R][C];
  int i,j,amount=0;
  printf("Please Enter 6 Words!!(Max 20 tabs):\n");
  for(i=0;i<R;i++)
  {
    fgets(Words[i],C,stdin);
  }
 amount=FindSimilarWords(Words);
 printf("The amount of the Similar words is: %d\n",amount);
}
[/PHP]

[PHP]
char FindSimilarWords(char findWord[R][C])
{
  int i,j,check=0;
  int counter=0;
  for(i=0;i<6;i++)
  {
    for(j=i+1;j<6;j++)
    {
    
     check=helpFind(findWord[i],findWord[j]);
     if(check==1)
     {
      break;
     }
    }
  
   counter++;
   
   puts(findWord[j]);
  }
  return counter;
  

}
[/PHP]

[PHP]
int helpFind(char findWord[],char findWord2[])
{
  int i,j;
  char save,sizeCount=0;
  int charCount=0;
  while(findWord[i]!='\0')
  {
   sizeCount++;
   i++;
  }
  for(i=0;i<'\0';i++)
  {
    for(j=0;j<'\0';j++)
    {
     
      if(findWord[i]==findWord2[j] || findWord[i]-32==findWord2[j] || findWord[i]+32==findWord2[j])
      {
        charCount++;
      }
    }
  }
  if(charCount==sizeCount)
  {
   return 1;
  }
  else
  {
   return 0;
  }
}
[/PHP]

---

