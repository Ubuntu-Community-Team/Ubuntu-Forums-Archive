---
title: "Error in an if statement-Java"
date: 2010-09-26
forum: Programming Talk
---

### Post by thomasrive on 2010-09-26
Hello everybody. I know the rules on posting homework, and I have read the FAQ. I'm not asking for somebody to do my program for me, I've already written the entire program but have been struck down by a bug which shouldn't be occurring. This is a simple GoFish program, and my problem resides in a misbehaving if statement.:confused:

[PHP]
 public static int[] cardArray = new int[39]; public static int[] cardSelected = new int[8];
 public void cardGame() {
        Random myRandom = new Random();
        //int cardDeal = myRandom.nextInt(40);

        int cardGiven =0;

        for(int i=0;i<8;i++){
            int cardDeal = myRandom.nextInt(39);
            cardGiven = myRandom.nextInt(8);
            cardArray[i] = cardDeal;
            cardSelected[i] = cardGiven;
    
        }
      
    }
    @Action
    public void fishing() {
        clear();
 
        cardGame();
        
        Random cardRandom = new Random();
        int alpha = cardRandom.nextInt(39);
       //Here Resides the misbehaving if Statement
        if(cardArray[alpha] == cardSelected[0] || cardArray[alpha] == cardSelected[1]
                || cardArray[alpha] == cardSelected[2]||cardArray[alpha] == cardSelected[3]||
                cardArray[alpha] == cardSelected[4]||cardArray[alpha] == cardSelected[5]||cardArray[alpha] == cardSelected[6]
                ||cardArray[alpha] == cardSelected[7]||cardArray[alpha] == cardSelected[8]){
            result.setText("You Won");
            String alpha2 = "";
            alpha2 += alpha;
            debug.setText(alpha2);
        }else{
            result.setText("");
            result.setText("Go Fish");
        }
[/PHP]

I have reviewed my code, and it is working only partly. When there is a match, the GUI I set up returns "You Won". However the problem occurs when there is no match made by the if statement, in which case nothing happens when the GUI is supposed to return "Go Fish". I'd be much appreciated if somebody could point me to the error if it exists. Made it using NetBeans.:P

---

### Post by dwhitney67 on 2010-09-26
Please consider the following, which was developed using vim.
```

      // ...

      Random  cardRandom = new Random();
      int     alpha      = cardRandom.nextInt(39);
      boolean isWinner   = false;

      for (int i = 0; i < cardSelected.length; ++i)
      {
         if (cardArray[alpha] == cardSelected[i])
         {
            isWinner = true;
            break;
         }
      }

      if (isWinner)
      {
         // player has won!
      }
      else
      {
         // go fish
      }

      // ...

```


P.S.  I just noticed that in your code, you declared cardSelected to be an array of 8 ints.  Those should be indexed using values ranging from 0 through 7.  Your conditional examines a non-existent value at position 8.

---

### Post by thomasrive on 2010-09-26
> **dwhitney67 said:**
> 
P.S.  I just noticed that in your code, you declared cardSelected to be an array of 8 ints.  Those should be indexed using values ranging from 0 through 7.  Your conditional examines a non-existent value at position 8.

Much obliged dwhitney. I don't think I would have caught that error since it did seem to work. Your streamlined code is appreciated, but I'll be fixing that tiny error for now. Thank you for your help. 
:KS

---

