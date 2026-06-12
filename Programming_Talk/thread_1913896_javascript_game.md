---
title: "javascript game"
date: 2012-01-23
forum: Programming Talk
---

### Post by mathiflip on 2012-01-23
Hi everybody, 
 
I'm learning javascript/jQuery. But I do not follow a structured book,  i'm just making a yahtzee game and search on google when I get stuck. 
For practice I made this Yahtzee game and everything seems to work. 
This is the first thing I made in javascript, so go easy on me.

**Now my question is:** (to the more experienced in js/jQuery) 
Would you guys check my code and tell me what I did good and what I did bad? 
Please point me to possible bugs, bad practice and security issues in my code. 
And give some tips to improve my code. 
I think that would help me a lot to get better. 
 
Also I _think_ everything works fine, but how can I be sure? 
I read something about unit testing, can this be done for this game and how would I approach it? 
 
I translated the code to english for the forum (original was dutch), so I hope  i didn't make a mistake there. Sorry for the little comments in the  code. 
 
Here is the html: 
```

<!DOCTYPE html> 
<html> 
<head> 
    <title>Yahtzee</title> 
    <link rel="icon" href="favicon.gif" type="image/gif" /> 
    <link href="stijl.css" rel="stylesheet" type="text/css" /> 
     <script src="[http://code.jquery.com/jquery-latest.js](http://code.jquery.com/jquery-latest.js)"></script> 
    <script src="yahtzee.js"></script> 
</head> 
<body> 
<div id="wrapper"> 
   <div> 
      <a href="index.html">Start over</a> 
   </div> 
    <div> 
       <input type="button" id="throwButton" value="Throw" /> 
    </div> 
        <div class="dice"> 
            <div id="dice1">&nbsp;</div> 
            <div class="holdline" id="holdline1"></div> 
            <div class="holdButtons"><input type="button"  disabled="disabled" class="holdButton" id="hold1" value="Hold"  /></div> 
        </div> 
        <div class="dice"> 
            <div id="dice2">&nbsp;</div> 
            <div class="holdline" id="holdline2"></div> 
            <div class="holdButtons"><input type="button"  disabled="disabled" class="holdButton" id="hold2" value="Hold"  /></div> 
        </div> 
        <div class="dice"> 
            <div id="dice3">&nbsp;</div> 
            <div class="holdline" id="holdline3"></div> 
            <div class="holdButtons"><input type="button"  disabled="disabled" class="holdButton" id="hold3" value="Hold"  /></div> 
        </div> 
        <div class="dice"> 
            <div id="dice4">&nbsp;</div> 
            <div class="holdline" id="holdline4"></div> 
            <div class="holdButtons"><input type="button"  disabled="disabled" class="holdButton" id="hold4" value="Hold"  /></div> 
        </div> 
        <div class="dice"> 
             <div id="dice5">&nbsp;</div> 
             <div class="holdline" id="holdline5"></div> 
             <div class="holdButtons"><input type="button"  disabled="disabled" class="holdButton" id="hold5" value="Hold"  /></div>   
        </div> 
    <table> 
      <tr><td>ones</td><td class="scoreSquare" id="0"></td></tr> 
      <tr><td>twos</td><td class="scoreSquare" id="1"></td></tr> 
      <tr><td>threes</td><td class="scoreSquare" id="2"></td></tr> 
      <tr><td>fours</td><td class="scoreSquare" id="3"></td></tr> 
      <tr><td>fives</td><td class="scoreSquare" id="4"></td></tr> 
      <tr><td>sixes</td><td class="scoreSquare" id="5"></td></tr> 
      <tr><td class="bold">&gt;63?</td><td  class="totalSquare" id="sixtyThree"></td></tr> 
      <tr><td class="bold">+35</td><td class="totalSquare" id="extra"></td></tr> 
      <tr><td class="bold">Subtotal</td><td class="totalSquare" id="subtotal"></td></tr> 
      <tr><td>&nbsp;</td><td>&nbsp;</td></tr> 
      <tr><td>3 of a kind</td><td class="scoreSquare" id="6"></td></tr> 
      <tr><td>4 of a kind</td><td class="scoreSquare" id="7"></td></tr> 
      <tr><td>full house</td><td class="scoreSquare" id="8"></td></tr> 
      <tr><td>small straight</td><td class="scoreSquare" id="9"></td></tr> 
      <tr><td>large straight</td><td class="scoreSquare" id="10"></td></tr> 
      <tr><td>yahtzee</td><td class="scoreSquare" id="11"></td></tr> 
      <tr><td>chance</td><td class="scoreSquare" id="12"></td></tr> 
      <tr><td class="bold">Subtotal</td><td class="totalSquare" id="subtotal2"></td></tr> 
      <tr><td class="bold">Yahtzee Bonus</td><td  class="totalSquare" id="yahtzeeBonus"></td></tr> 
      <tr><td class="bold">Total</td><td class="totalSquare" id="totalScore"></td></tr> 
    </table> 
</div> 
</body> 
</html>

```and the js: 
```
/*  
 * Yahtzee in javascript/jQuery 
 * Made by mathiflip 
 * december 2011 
 */ 
 
/* 
 * global variabels 
 */ 
var dices = new Array(0,0,0,0,0); 
var hold = new Array(0,0,0,0,0); 
var scoreArray = new Array(-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1); 
var largeStraightArray = new Array(new Array(2,3,4,5,6),new Array(1,2,3,4,5)); 
var turn = 1; 
var timesThrown = 0; 
var scoreLock = true; 
var yahtzeeBonus = 0; 
var subtotal = new Array(0,0); 
var total = 0; 
 
 
/* 
 * Start declaration of all the functions 
 */ 
function getDices(){ 
    for (i=1;i<=5;i++) { 
        $("#dice"+i).html(dices[i-1]); 
    } 
} 
function throwDices(){ 
    for (i=0;i<5;i++) { 
        if(hold[i]==0) 
            dices[i] = Math.floor(Math.random()*6)+1; 
    } 
} 
function setHold(dsNummer){ 
    knop = $("#hold"+dsNummer); 
    value = knop.val(); 
    i = parseInt(dsNummer)-1; 
     
    if(value=="Hold"){ 
        hold[i]=1; 
        $("#holdline"+dsNummer).css("background-color","#000"); 
        knop.val("Unhold"); 
    } else{ 
        hold[i]=0; 
        $("#holdline"+dsNummer).css("background-color","transparent"); 
        knop.val("Hold"); 
    } 
} 
function removeHoldLines(){ 
   for(i=1;i<6;i++){ 
      $("#holdline"+i).css("background-color","transparent"); 
        $("#hold"+i).val("Hold"); 
   } 
} 
function setScore(veld, score){ 
   $("#"+veld).html(score); 
} 
function checkScore(eyes){ 
   var score=0; 
       
   for(i=0;i<6;i++){ 
      if(dices[i]==eyes) 
         score+=eyes; 
   } 
   return score; 
} 
function sortNumber(a,b){ 
   return a-b; 
} 
 
function checkXOfAKind(x){ 
   var same = 1; 
   dices.sort(sortNumber); 
   var last = dices[0]; 
    
   for(i=1; i<5; i++){ 
      if(same==x) 
         break; 
      if(last===dices[i]) 
         same++; 
      else 
         same=1; 
          
      last = dices[i]; 
   } 
    
   return same; 
} 
function threeOfAKind(){ 
   var score=0; 
   var same = checkXOfAKind(3); 
    
   if(same>=3) 
      score=chance(); 
       
   return score; 
} 
function fourOfAKind(){ 
   var score=0; 
   var same = checkXOfAKind(4); 
    
   if(same>=4) 
      score=chance(); 
       
   return score; 
} 
function fullHouse(){ 
   var score=0; 
   dices.sort(sortNumber); 
   var count = 1; 
   var found3 = false, found2 = false; 
   for (i=1; i < 5;i++) 
   { 
      if (dices[i] == dices[i-1])  
         count++; 
      else 
      { 
         if (count == 3) 
            found3 = true; 
         else if (count == 2) 
            found2 = true; 
         count=1; 
      } 
   } 
   if (count == 3) 
      found3 = true; 
   else if (count == 2) 
      found2 = true; 
   if (found3 && found2) 
      score=25; 
    
   return score; 
} 
function smallStraight(){ 
   var score=0; 
   var same = false; 
   dices.sort(sortNumber); 
    
   var curSeqLen=1; 
    var lastDie=dices[0]; 
     
    // if the lowest number is a 4, or the highest number is a 3, it cannot be small straight 
    if (dices[0] >= 4 || dices[4] <= 3) 
       same = false; 
  
    for (i = 1; i < 5; i++) { 
        // the current die is one greater than the last one, the numbers are in sequence 
        if (dices[i] == lastDie+1){ 
            curSeqLen++; 
        } 
        else if (dices[i] == lastDie){} 
        // the consecutive dice are not in order, still might be a straight in there 
        else{ 
            curSeqLen=1; 
        } 
         
        if (curSeqLen >=4) 
           same = true; 
            
        lastDie = dices[i]; 
    } 
 
   if(same) 
      score=30; 
    
   return score; 
} 
function largeStraight(){ 
   var score=0; 
   dices.sort(sortNumber); 
    
   var same = false; 
   var hetzelfde2 = false; 
    
   for(i=0;i<5;i++){ 
      if(largeStraightArray[0][i]==dices[i]){ 
         same = true; 
      } 
      else { 
         same = false; 
         break; 
      } 
   } 
   for(i=0;i<5;i++){ 
      if(largeStraightArray[1][i]==dices[i]){ 
         hetzelfde2 = true; 
      } 
      else { 
         hetzelfde2 = false; 
         break; 
      } 
   } 
   if(same || hetzelfde2) 
      score=40; 
    
   return score; 
} 
//check whole dicesArray against it's first element, every element has to be the same 
function checkYahtzee(){ 
   for(i=0;i<5;i++){ 
      if(dices[0]===dices[i]) 
         same = true; 
      else { 
         same = false; 
         break; 
      } 
   } 
   if(same) 
      return true; 
   else 
      return false; 
} 
function chance(){ 
   var score=0; 
   dices.forEach(function(x){score+=x;}); 
    
   return score; 
} 
function getSubtotal(id){ 
   var score = 0; 
   var halt = 6; 
   if(id===1){ 
      id=6; 
      halt=13; 
   } 
   for(i=id;i<halt;i++){ 
      (scoreArray[i]===-1)? plusScore = 0 : plusScore = scoreArray[i]; 
      score += plusScore; 
   } 
    
   return score; 
} 
function getTotal(){ 
   return subtotal[0]+subtotal[1]+yahtzeeBonus; 
} 
 
 
//start call functions when page is loaded 
$(function(){ 
       $("#throwButton").click(function(){ 
          scoreLock = false; 
           
           if(timesThrown==0) 
               $(".holdButton").attr("disabled","disabled"); 
                
           if(timesThrown<3){ 
              $(".holdButton").removeAttr("disabled"); 
               throwDices(); 
               getDices(); 
                
               ++timesThrown; 
           } 
           if(timesThrown==3){ 
               //reset everything 
               $(this).attr("disabled","disabled"); 
               $(".holdButton").attr("disabled","disabled"); 
               hold = Array(0,0,0,0,0); 
               timesThrown = 0; 
               for (i=1;i<=5;i++) { 
                   $("#hold"+i).val("Hold") 
                   $("#holdline"+i).css("background-color","transparent") 
               }          
           } 
       }); 
        
       $(".holdButton").click(function(){ 
           i = $(this).attr("id"); 
           nr = i.substring(4); 
           //console.log(nr); 
           setHold(nr); 
       }); 
        
        
       /* 
        * When a scoreSquare is clicked then fill in teh score and and  the turn, reset timesThrown, hold array and hold buttons, if 13 turns  have passed then end the game' 
        */ 
       $(".scoreSquare").click(function(){ 
          if(turn==13){ 
           $("#throwButton").val('Game finished').attr("disabled","disabled");    
         } else { 
          $("#throwButton").removeAttr('disabled'); 
         } 
         if(checkYahtzee() && scoreArray[11]===50){ 
            yahtzeeBonus +=100; 
         } 
         timesThrown = 0; 
         $(".holdButton").attr("disabled","disabled"); 
           hold = Array(0,0,0,0,0); 
           removeHoldLines(); 
         id = parseInt($(this).attr("id")); 
          
         if($(this).html()=='' && !scoreLock && scoreArray[id]===-1){ 
             
            //console.log(id); 
            switch(id){ 
               case 6: 
                  scoreArray[6] = threeOfAKind(); 
                  break; 
               case 7: 
                  scoreArray[7] = fourOfAKind(); 
                  break; 
               case 8: 
                  scoreArray[8] = fullHouse(); 
                  break; 
               case 9: 
                  scoreArray[9] = smallStraight(); 
                  break; 
               case 10: 
                  scoreArray[10] = largeStraight(); 
                  break; 
               case 11: 
                  (checkYahtzee()) ? scoreArray[11] = 50 : scoreArray[11] = 0; 
                  break; 
               case 12: 
                  scoreArray[12] = chance(); 
                  break; 
                
               default: 
                  scoreArray[id] = checkScore(id+1); 
            } 
            $("#"+id).html(scoreArray[id]); 
            scoreLock = true; 
             
             
            subtotal[0] = getSubtotal(0); 
            $("#sixtyThree").html(subtotal[0]); 
            if(subtotal[0]>=63){ 
               $("#extra").html('35'); 
               subtotal[0] += 35; 
            } else { 
               $("#extra").html('0'); 
            } 
            $("#subtotal").html(subtotal[0]); 
            subtotal[1] = getSubtotal(1); 
            $("#yahtzeeBonus").html(yahtzeeBonus); 
            $("#subtotal2").html(subtotal[1]); 
            total = getTotal(); 
            $("#totalScore").html(total); 
             
             
             
            ++turn; 
         } 
      }); 
}); 
```if you just wanna check it out:
[http://bit.ly/xJIMtA](http://bit.ly/xJIMtA)

---

