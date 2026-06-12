---
title: "Input players"
date: 2011-11-19
forum: Programming Talk
---

### Post by DayNight on 2011-11-19
[FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2][FONT=Courier New][SIZE=2][LEFT]SAMPLE 1:
Enter number of players (1-3) > 3
Enter Name of Player A > adrian
Enter Name of Player B > Bell
Enter Name of Player C > carol

SAMPLE 2
Enter number of players (1-3) > 2
Enter Name of Player A > He
*** NAME TOO SHORT!
Enter Name of Player A > Addy[/LEFT]
Enter Name of Player B > Fed


The above is what is required to print in my Java. However, i do now know how to make use of array in this form.
Do give me some tips and suggestion of how it should be done.
 

this is my current progress: 
[B][SIZE=1][COLOR=#7f0055][SIZE=1][COLOR=#7f0055]
[LEFT]public[/B][/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1] [/SIZE]**[SIZE=1][COLOR=#7f0055][SIZE=1][COLOR=#7f0055]class**[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1] BlackJackGame {
[/SIZE]**[SIZE=1][COLOR=#7f0055][SIZE=1][COLOR=#7f0055]public**[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1] [/SIZE]**[SIZE=1][COLOR=#7f0055][SIZE=1][COLOR=#7f0055]void**[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1] start() {

String [] Player = [/SIZE]**[SIZE=1][COLOR=#7f0055][SIZE=1][COLOR=#7f0055]new**[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1] String [3];

Player[0] = [/SIZE][SIZE=1][COLOR=#2a00ff][SIZE=1][COLOR=#2a00ff]"Player A"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1];
Player[1] = [/SIZE][SIZE=1][COLOR=#2a00ff][SIZE=1][COLOR=#2a00ff]"Player B"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1];
Player[2] = [/SIZE][SIZE=1][COLOR=#2a00ff][SIZE=1][COLOR=#2a00ff]"Player C"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1];



System.[/SIZE]*[SIZE=1][COLOR=#0000c0][SIZE=1][COLOR=#0000c0]out*[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1].println([/SIZE][SIZE=1][COLOR=#2a00ff][SIZE=1][COLOR=#2a00ff]"B L A C K J A C K "[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1]);
System.[/SIZE][I][SIZE=1][COLOR=#0000c0][SIZE=1][COLOR=#0000c0]out[/LEFT]
[/I][/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1][LEFT].println([/SIZE][SIZE=1][COLOR=#2a00ff][SIZE=1][COLOR=#2a00ff]"========================================================"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1]);

[/SIZE][SIZE=1][COLOR=#3f7f5f][SIZE=1][COLOR=#3f7f5f]// input number of player[/LEFT]
[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1][LEFT][/SIZE]**[SIZE=1][COLOR=#7f0055][SIZE=1][COLOR=#7f0055]for**[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1] ([/SIZE]**[SIZE=1][COLOR=#7f0055][SIZE=1][COLOR=#7f0055]int**[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1] i = 0; i < 4; i++) {
[/SIZE]**[SIZE=1][COLOR=#7f0055][SIZE=1][COLOR=#7f0055]int**[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1] numPlayer = Keyboard
.*readInt*([/SIZE][SIZE=1][COLOR=#2a00ff][SIZE=1][COLOR=#2a00ff]"Enter number of players (1-3) > "[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1]);
[/SIZE]**[SIZE=1][COLOR=#7f0055][SIZE=1][COLOR=#7f0055]if**[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1] (numPlayer > 3) {
System.[/SIZE]*[SIZE=1][COLOR=#0000c0][SIZE=1][COLOR=#0000c0]out*[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1].println([/SIZE][SIZE=1][COLOR=#2a00ff][SIZE=1][COLOR=#2a00ff]"Maximum of 3 players in this game"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1]);
}
[/SIZE]**[SIZE=1][COLOR=#7f0055][SIZE=1][COLOR=#7f0055]else**[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1] 
[/SIZE]**[SIZE=1][COLOR=#7f0055][SIZE=1][COLOR=#7f0055]if**[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1] (numPlayer < 1) {
System.[/SIZE]*[SIZE=1][COLOR=#0000c0][SIZE=1][COLOR=#0000c0]out*[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1].println([/SIZE][SIZE=1][COLOR=#2a00ff][SIZE=1][COLOR=#2a00ff]"Insufficient players"[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1]);

[/SIZE][SIZE=1][COLOR=#3f7f5f][SIZE=1][COLOR=#3f7f5f]//Enter name of Players

[/LEFT]
[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1]
[/SIZE][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT]

---

### Post by davetv on 2011-11-19
Hi,

I'm not an expert in java (c is more my thing) but for a start :-

> for (int i = 0; i < 4; i++) {

will iterate 4 times
i=0
i=1
i=2
i=3

I don't think this is what the programmatic intention is.

You shouldn't have the "enter number of players bit" and the test inside the "for" loop or it will be asked to be entered 4 times.

After we know how many players there are, we only need to ask their names, this is the only bit that should be in the for loop - which should be for(i=0; i<numPlayer; i++) {...

Not a java expert again but here is a correction of your code -

public
class BlackJackGame {
publicvoid start() {

String [] Player = new String [3];

Player[0] = "Player A";
Player[1] = "Player B";
Player[2] = "Player C";



System.out.println("B L A C K J A C K ");
System.out

.println(
"================================================= =======");

// input number of player
int numPlayer = Keyboard
.readInt("Enter number of players (1-3) > ");
if (numPlayer > 3) {
  System.out.println("Maximum of 3 players in this game");
}
else
  if (numPlayer < 1) {
    System.out.println("Insufficient players");
  }
// now iterate player count and get names
for (int i = 0; i < numPlayer; i++) {
//Enter name of Players

You would probably want some sort of "exit" statement (not sure in java) if the numPlayer value was invalid due to the 2 tests (min and max), otherwise it will still ask for names if numPlayer exceeded max. If numPlayer is <=0 - the for loop won't execute (i is never < 0).

---

