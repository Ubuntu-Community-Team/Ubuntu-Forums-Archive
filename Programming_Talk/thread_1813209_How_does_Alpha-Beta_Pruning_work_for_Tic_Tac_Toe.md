---
title: "How does Alpha-Beta Pruning work for Tic Tac Toe?"
date: 2011-07-27
forum: Programming Talk
---

### Post by skytreader on 2011-07-27
So, I have already created a minimax method for tic tac toe. However, I don't get how AB-Pruning can work for it. Let me explain.

The way I understand minimax: generate a game tree all the way to the endgames. If a branch can lead to a (win|lose) for (max|min), pursue. Else, pick another branch.

The way I understand AB-Pruning: The moment a branch becomes (less|greater) than current (max|min), discard.

I don't see how ABP can help minimax. Minimax "passes" through the tree twice: one to generate the endgames and another one to "ripple up" the values of endgames to the "caller" nodes. So, for ABP to know if a branch becomes (less|greater) than current (max|min), it still needs to generate the endgames and then wait for the ripple up.

I already have this code:

```

int computer_move(char** board, char piece1, char piece2){
   //Some code here...

   int max = -1;
   int min = 1;
   
   for(i = 0; i < blankcount; i++){
      //Will be given to the recursive call
      char** clonechild = (char**) malloc(sizeof(char*) * 3);
      int j;
      for(j = 0; j < 3; j++){
         clonechild[j] = (char*) malloc(sizeof(char) * 3);
      }
      //All children has been pre-generated. Recurse on each one.
      copyboard(children[i], clonechild);
      int nextmove = computer_move(clonechild, piece2, piece1);
      
      //In other words: if this node is greater than current min
      //ignore. But still, we generated endgames.
      if(piece1 == PLAYER1 && nextmove < min){
         min = nextmove;
         theindex = i;
      }
      //In other words: if this node is less than current max
      //ignore. But still, we generated endgames.
      else if(piece1 == PLAYER2 && nextmove > max){
         max = nextmove;
         theindex = i;
      }
   }

   //...and then some more.
}

```

So it seems to me that I'm already doing ABP (or at least, how I understand it).

Thanks to anyone who'd take the time to explain.

---

### Post by era86 on 2011-07-27
It's been a very long time and my understanding might be off, but I'll try.  From my understanding you generate all possible moves with in a tree for two players.  You put, for example, 0 for loss, 10 for tie, and 20 for win as your score at the leaves of the tree.  Depending on the player making the move, you select the min or max based on the score at each endgame.

With AB-pruning, you optimize the search part of the algorithm by ignoring any subtree that is NEVER going to be better than other moves.  In that way, you can reduce your search time fairly significantly because you prune out all the unnecessary subtrees.

Again, I could be wrong.  Goodluck and followup on this because I'm curious.  Haha

---

### Post by nvteighen on 2011-07-28
If you know Python, look at this code from my PycTacToe project: [http://bazaar.launchpad.net/~evigo/pyctactoe/trunk/view/head:/pttengine.py#L494](http://bazaar.launchpad.net/~evigo/pyctactoe/trunk/view/head:/pttengine.py#L494)

It's a bit weird in some respects. It's an alpha-beta pruned negamax algorithm that works for Tic-Tac-Toe, Connect-4 and similar games without any known issues.

For this, the "entry" point would be the Alicia.decide method. Alicia.generate_children is left blank, as this has to be determined for each game. E.g. the way you generate legal children boards in Connect-4 is different than in Tic-Tac-Toe (Connect-4 has "gravity").

For the Tic-Tac-Toe evaluator, look here: [http://bazaar.launchpad.net/~evigo/pyctactoe/trunk/view/head:/pttgames/tictactoe.py#L80](http://bazaar.launchpad.net/~evigo/pyctactoe/trunk/view/head:/pttgames/tictactoe.py#L80)

---

### Post by NovaAesa on 2011-07-28
When you run minmax normally, you can actually generate the tree and "ripple up" at the same time (just use a DFS). You pretty much do the same thing when you add in the alpha-beta pruning. The tree is built implicitly in the call stack.

---

### Post by Kschikan on 2011-07-28
I think the key point you're missing is that the "bubble-up" from minimax and the pruning from Alpha-Beta happen concurrently. I always find an example helps me, so here goes.

Let's say you're creating your tree, and you get to a node with 2 or more children. As part of your minimax, you go down the leftmost child, and it returns that the value for that child is a WIN/LOSE (depends on whether that node is getting minimized or maximized). Well, you already know now that whatever the values of the other nodes are, the optimal path from the current node is that leftmost child. Since you already know this, there's no point in traversing the other children.

Of course, you don't know ahead of time that the leftmost child is going to be a minimax optimal node - it could be any of the children, or none of the children. But even if you save having to traverse one path, that can be a significant savings. 

With tic-tac-toe it's not such a big deal, but on games like chess AB-pruning frequently uses a threshold for min/max, since you rarely explore the entire tree, just finding a path that is "good enough" means you don't need to traverse the rest of the children. Of course, "good enough" is debatable for different games.

Hope that helped.

---

### Post by skytreader on 2011-08-02
Ok. Thanks everyone. But Kschikan got what I failed to understand. Ok. In ABP, prune the *brothers* of the node the moment its parent branch becomes obviously (less|greater) than current (max|min). (I though I'd have to prune from the parent, hence my seeing no sense in it.)

Thanks again!

---

