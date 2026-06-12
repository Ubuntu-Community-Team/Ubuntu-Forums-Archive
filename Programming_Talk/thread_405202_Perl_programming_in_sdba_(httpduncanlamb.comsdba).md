---
title: "Perl programming in sdba (http://duncanlamb.com/sdba/)"
date: 2007-04-09
forum: Programming Talk
---

### Post by JRaz on 2007-04-09
I'm not sure if this is more of a perl or sdba question so bare with me. Basically I'm attempting to write a msn bot in sdba ([http://duncanlamb.com/sdba/)](http://duncanlamb.com/sdba/)). Sdba allows you to write pages in perl as if the msn chat was a web server and each response was like a web page.

Anyway the bot I am making is a hangman game which will generate a random word from a database and then present the game to the user, the user will then send a message containing a character until he/she dies or correctly guesses the word.

The problem is however that the variables are global to all users, so Player A would initiate a conversation and a game. Then Player B decides to start a game too, however he would end up getting Player A's game and progress since he would be using his variables.

I initially thought of making every non-array variable an array and every array a 2d array with the users email address as the index, however while I cant think of why it wouldn't work I had trouble implementing such a method.

Anyway I've rambled for long enough so ill just post my code bellow and if anyone can think of a way to implement the index method i talked about or possibly a better method I'm all ears. Thanks in advance.

```
#HEAD:play
<%
if(!$word){
 $word='hangman';
 @char=split(//,$word);
}

#reduce msg to 1 char lower case
$msg=lc substr($INCOMINGMSG,0,1);

#if alpabetic then add to guesses
if($msg=~/[a-z]/){
 #clear msg if its a repeat
 for($a=0;$a<@guess;$a++){
  if($msg eq $guess[$a]){
   $msg='';
  }
 }

 #if msg nt clear then add it to array
 if($msg){
 # push(@guess,$msg);
   $guess[$a]=$msg;
 }
}

imecho "@guess\n\n";

for($a=0;$a<@char;$a++){
 $letter='_';
 for($b=0;$b<@guess;$b++){
  if($char[$a] eq $guess[$b]){
   $letter=$char[$a];
  }
 }
 imecho $letter;
}

$NEXTPAGE='game.first';
%>
```

---

### Post by JRaz on 2007-04-10
Well I managed to figure out that problem and am almost done I'm my implementation of hangman, I just have one hurdle left. I need to generate a random word from a large a dictionary as possible.

So I have two choices, ideally I would like to be able to generate a random word form aspell or less ideally does anyone know a good word list I can dumb into a mysql table and just read off a random row.

Any help would be appreciated, many thanks.

PS If anyone is interested I am happy to post the code, but be warned it aint pretty lol :P

---

### Post by JRaz on 2007-04-11
Well the bot is pretty much up and running, if anyone would like to add it the address is [email]hangraz@hotmail.com[/email] and he runs on the MSN network.

---

