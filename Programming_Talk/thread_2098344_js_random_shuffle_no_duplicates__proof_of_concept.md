---
title: "js random shuffle no duplicates | proof of concept"
date: 2012-12-26
forum: Programming Talk
---

### Post by maclenin on 2012-12-26
Using javascript, I wanted to (randomly) shuffle a sequential set of numbers (e.g. 1 to x) and then insert the entire shuffled set into a web-based grid. This seems to facilitate the job (while eliminating duplicates):

var rNDM=[];  [COLOR="DarkGreen"]//target array for shuffled unique set.[/COLOR]
var DrNDM=[];  [COLOR="DarkGreen"]//'optional' array for duplicates.[/COLOR]
var rNG=25;  [COLOR="DarkGreen"]//largest number in set (i.e. shuffle numbers 1 through 25).[/COLOR]

while (rNDM.length<rNG) {  [COLOR="DarkGreen"]//loop until target array contains a full set of shuffled unique numbers.[/COLOR]
rnd=Math.floor((Math.random()*rNG)+1);  [COLOR="DarkGreen"]//generate a random number between (and including) 1 and the largest number in your defined set (e.g. 25).[/COLOR]
if (rNDM.length===0) {[COLOR="DarkGreen"]//if the target array is empty...[/COLOR] 
rNDM.push(rnd);} [COLOR="DarkGreen"]//...add the random number to the target array.[/COLOR]
else { [COLOR="DarkGreen"]//else (if) the target array already contains at least one number...[/COLOR]
if (rNDM.indexOf(rnd) === -1) {  [COLOR="DarkGreen"]//...verify that the random number just generated does NOT already exist in the target array.[/COLOR]
rNDM.push(rnd);}   [COLOR="DarkGreen"]//if the random number does NOT exist in the target array, add the random number to the target array.[/COLOR]
else {[COLOR="DarkGreen"]//optional (perhaps) - if the random number DOES already exist in the target array...[/COLOR]
DrNDM.push(rnd);} [COLOR="DarkGreen"]//...send the random number, instead, to the duplicates array.[/COLOR]
}} [COLOR="DarkGreen"]//close.[/COLOR]

console.log(rNDM);  [COLOR="DarkOrange"]//...does it work?[/COLOR]

Read here: [Fisher-Yates]("http://sedition.com/perl/javascript-fy.html")
Tested here: [jsBin]("http://jsbin.com/#javascript,html,live")

Thanks for any thoughts.

P.S. Will mull non-sequential set shuffles, as well.

---

