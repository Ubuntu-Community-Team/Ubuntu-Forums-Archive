---
title: "[java] my KeyListener not working"
date: 2012-09-17
forum: Programming Talk
---

### Post by coolglen on 2012-09-17
I'm very new to programing and I'm trying to follow a tutorial video in the tutorial I need to make a KeyListener Ive written the code but I have gotten something wrong somewhere and the KeyListener is not receiving any input can someone help me find out why?

```
public class KeyInput extends KeyAdapter implements KeyListener{

    Player p;
    
    public KeyInput(Player p){
        this.p = p;
    }
    
    public void KeyPressed(KeyEvent e){
        p.KeyPressed(e);
    
    }
    
    public void KeyReleased(KeyEvent e){
        p.KeyReleased(e);
    
    }
}

``````
public class Player extends GlobalPosition {

    private String playerImage = "/res/Player.png";
    
    public static int velX = 0;
    public static int velY = 0;
    
    public Player(int x, int y) {
        super(x, y);
        
    }

    public void update(){
        x += velX;
        y += velY;
    }
    
    public void KeyPressed(KeyEvent e){
        int Key = e.getKeyCode();
        
        if(Key==KeyEvent.VK_D){
            System.out.println("input received");
            velX = 5;
        }else if(Key==KeyEvent.VK_A){
            velX = -5;
        }else if(Key==KeyEvent.VK_S){
            velY = 5;
        }else if(Key==KeyEvent.VK_W){
            velY = -5;
        }
            
    }
    public void KeyReleased(KeyEvent e){
        int Key = e.getKeyCode();
        
        if(Key==KeyEvent.VK_D){
            velX = 0;
        }else if(Key==KeyEvent.VK_A){
            velX = 0;
        }else if(Key==KeyEvent.VK_S){
            velY = 0;
        }else if(Key==KeyEvent.VK_W){
            velY = 0;
        }
    }
    
    public void draw(Graphics2D g2d){
        g2d.drawImage(getPlayerImage(), x, y, null);
    }
    
    public Image getPlayerImage(){
        ImageIcon i = new ImageIcon(getClass().getResource(playerImage));
        return i.getImage();
    }
}
``````
public class Game extends JPanel implements ActionListener{
    private static final long serialVersionUID = 1L;
    
    
    private String bgImage = "/res/bg.png";
    
    Timer gameLoopTimer;
    Player p;
    
    public Game(){
        setFocusable(true);
        
        gameLoopTimer = new Timer(10, this);
        gameLoopTimer.start();
        
        p = new Player(300, 200);
        
        addKeyListener(new KeyInput(p));
        
    }
    
```

---

### Post by PaulM1985 on 2012-09-17
KeyAdapter implements KeyListener, so in your definition of your KeyInput class you don't need to have "implements KeyListnener" since this is already done by the KeyAdapter.

Does your Game panel definitely have focus?  You might want to use some of the API functions to check if you panel has the focus and "grab" it if not.

Paul

---

### Post by coolglen on 2012-09-17
Thanks for the reply, I forgot to delete the implements KeyListener i had it there to try to get it to work, like i said I'm very new to java how would I go about using the API to check if it has focus?

---

### Post by PaulM1985 on 2012-09-17
Here is a link to the API:

[http://docs.oracle.com/javase/6/docs/api/](http://docs.oracle.com/javase/6/docs/api/)

You can find the entry for JPanel in the navigation frame on the left hand side.  Clicking on it should show you a description of the functions available for a JPanel aswell as links to the classes it inherits from.

I'll not tell you too much so that you can learn to look at the API yourself.  Hopefully this should sort you out.  Post again if you get stuck.

Paul

---

