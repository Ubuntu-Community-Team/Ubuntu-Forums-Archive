---
title: "[Project] Python Poker Bot"
date: 2012-01-01
forum: Programming Talk
---

### Post by chevloschelios on 2012-01-01
[COLOR=#1E90FF]Hi guys, I decided to create Python Zynga Poker bot

If is anybody interested give me PM
[/COLOR]
Thank you

---

### Post by JDShu on 2012-01-01
If you want to write it, then write it. Nobody is stopping you :)

---

### Post by PaulM1985 on 2012-01-02
Poker playing robots are not trivial.  They are very different to games like chess and draughts where you can create a game tree and perform min-max.  I suggest you really research this area, rather than just jumping in.

Paul

---

### Post by Bodsda on 2012-01-02
> **PaulM1985 said:**
> Poker playing robots are not trivial.  They are very different to games like chess and draughts where you can create a game tree and perform min-max.  I suggest you really research this area, rather than just jumping in.

Paul


Or jump in and research solutions to the problems that you encounter.

Bodsda

---

### Post by KdotJ on 2012-01-02
> **Bodsda said:**
> Or jump in and research solutions to the problems that you encounter.

+1 to this! I prefer this way lol, if I decided to research everything theoretically through and through before I even started on it, I'd most likely lose interest.

---

### Post by chevloschelios on 2012-01-02
Hi guys,

thank you for your replies

My biggest problem is how to connected to that shi##y flash games ...
Do you have any ideas. (I dont want to make something like - Make screen shot and then compare the hash with other to get cards ....)

---

### Post by PaulM1985 on 2012-01-02
> **Bodsda said:**
> Or jump in and research solutions to the problems that you encounter.

Bodsda

The reason I say this is that if you want to create something that is truely intelligent you are going to have to do some research.  

I have spent the past 6 months reading up on this subject and there are lots of studies out there showing that this is not a simple area.  It is very easy to create a poker player which will place only value bets trying to achieve an above average return, but these can be easily exploited and end up being very one dimensional in their playing strategy.

Why do you want to create a poker bot?

Paul

---

### Post by chevloschelios on 2012-01-02
Just for fun. I just wanna make some "Artificial Inteligence"

---

### Post by PaulM1985 on 2012-01-02
So why connect to flash games?  Why not write your own game and get people to play it?  Writing the game is alot less hassle than writing the AI that goes with it.

---

### Post by chevloschelios on 2012-01-02
But is it possible to connect it with flash games ?

---

### Post by nvteighen on 2012-01-03
> **chevloschelios said:**
> But is it possible to connect it with flash games ?

Define "connect".

If you mean interfacing with those Flash games via an API, I highly doubt that's possible. Never heard about Flash applications that have some sort of API... The only plausible thing I can think of is that the Flash game itself interfaced with some server or whatever that does have a public interface... in that case, you would have your program to interface with that backend, not with the Flash frontend.

If you mean "playing by mimmicking a human player's actions", you're onto a very very hard task. You'd have to somehow teach your program to recognize the visual patterns of the Flash game in order to know what's happening on the game and then make it somehow be able to enter input to the Flash game... However, I bet the web browser and Flash will prevent you to do that, for security reasons...

If you want to work on some AI, please take a look at my PycTacToe project... Precisely today I've encountered a very nasty issue regarding the AI engine: it's terribly slow. I knew it was, but for Tic-Tac-Toe and Connect-4, the slowness was somewhat tolerable... For Gomoku, it's unbearable, taking almost a minute to perform a move. I don't think it's Python's fault, but for sure it's my implementation.

---

