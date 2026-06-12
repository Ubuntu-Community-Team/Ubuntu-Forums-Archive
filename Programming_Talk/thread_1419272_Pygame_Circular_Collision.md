---
title: "Pygame Circular Collision"
date: 2010-03-01
forum: Programming Talk
---

### Post by Penguin Guy on 2010-03-01
SOLVED: Turns out the rect was set wrong - I'd set it using [FONT="Courier New"]rect = (x, y, w, h)[/FONT] rather than [FONT="Courier New"]rect = pygame.Rect(x, y, w, h)[/FONT].

----------------------------------------

I've been trying to detect if a object 'player' is in contact with any opponents in Pygame. I'm using the function [FONT="Courier New"]pygame.sprite.collide_circle()[/FONT] - although obviously incorrectly. I couldn't find much documentation on it, and what documentation I found, I didn't understand. I'd be grateful if somebody could give me a pointer.

Here's the relevant code (full package attached):
**[PYTHON]**
[PHP]
# Update all opponents
for opponent in opponents:
    opponent.update(time_passed, player.size)
    if pygame.sprite.collide_circle(player, opponent):  # If opponent is in contact with player:
        print 'Contest:', opponent.size, player.size
        if opponent.size > player.size: # Biggest contestant eats the other
            opponent.eat(player)
            game_over()
        if opponent.size < player.size: 
            player.eat(opponent)
[/PHP]

The output I get is:
```

[B]Contest: 75 78
Contest: 65 78
Contest: 65 78
Contest: 75 78
Contest: 78 78
Contest: 53 78[/B]
Contest: 75 78
Contest: 65 78
Contest: 65 78
Contest: 75 78
Contest: 78 78
Contest: 53 78
**...**

```
(a.k.a. recurring output of the highlighted text)

I'm 99% sure that [FONT="Courier New"]pygame.sprite.collide_circle(player, opponent)[/FONT] is returning [FONT="Courier New"]True[/FONT] regardless of the positions of player and opponent.

---

### Post by Tony Flury on 2010-03-01
Obvious question - did you set the rect and/or radius attributes correctly on the sprites ?

---

### Post by Penguin Guy on 2010-03-02
> **Tony Flury said:**
> Obvious question - did you set the rect and/or radius attributes correctly on the sprites ?
Ahh, it seems I've set [FONT="Courier New"]rect[/FONT] incorrectly - thanks!

---

