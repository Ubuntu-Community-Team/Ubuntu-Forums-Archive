---
title: "Adding and removing panels on an applet"
date: 2012-01-19
forum: Programming Talk
---

### Post by PaulM1985 on 2012-01-19
Hi

I am having some trouble with Java applets and I was wondering if someone could help me out.

I have a game which works fine as a desktop, but doesn't seem to work properly as an applet.  The general cycle is as follows:

1 - Applet starts up and a NewGamePanel is added to the applet
2 - The user enters their name and clicks on the Start button on the NewGamePanel, which sets the "canStart" member of NewGamePanel to true.
3 - The applet picks up that this has been clicked, removes the NewGamePanel and puts the actual game panel in place.

The problem that I am having is that once the Start button is clicked, the applet seems to lock up, like the new panel is placed on the applet, but is not rendered.  Below is my applet code:

```

/*
 * To change this template, choose Tools | Templates
 * and open the template in the editor.
 */

package pokerui.applet;

import cardslib.DuplicatePlayerException;
import cardslib.Player;
import cardslib.PokerFacade;
import javax.swing.JApplet;
import pokerui.PlayAgainstComputerPanel;

/**
 *
 * @author paul
 */
public class PokerApplet extends JApplet implements Runnable {

    final static int START_MONEY = 500;

    NewGamePanel mNewGamePanel;
    PlayAgainstComputerPanel mPanel;
    PokerFacade mFacade;
    
    /**
     * Initialization method that will be called after the applet is loaded
     * into the browser.
     *
     */
    public void init() {
        // TODO start asynchronous download of heavy resources
        super.init();
        mFacade = new PokerFacade();
        mPanel = new PlayAgainstComputerPanel();
    }

    // TODO overwrite start(), stop() and destroy() methods
    public void start()
    {
        try
        {
            // Temp: Add some players
            mFacade.addPlayer(new Player("PaulAI", START_MONEY, true));
        }
        catch (DuplicatePlayerException e)
        {
            // TODO: Prevent this
        }

        mNewGamePanel = new NewGamePanel(this);
        add(mNewGamePanel);

        Thread t = new Thread(this);
        t.start();
    }

    public void run()
    {
        while (!mNewGamePanel.canStart)
        {
            try {Thread.sleep(50); } catch (Exception e) {}
        }

        // This remove doesn't seem to work...

        remove(mNewGamePanel);
        mPanel.setPokerFacade(mFacade);

        // From here the panel doesn't seem to be displayed...

        add(mPanel);

        while (true)
        {
            mPanel.updateInterface();
            try {Thread.sleep(50); } catch (Exception e) {}
        }
    }

    boolean addPlayer(String playersName)
    {
        boolean returnValue;
        try
        {
            mFacade.addPlayer(new Player(playersName, START_MONEY, false));

            returnValue = true;
        }
        catch (DuplicatePlayerException e)
        {
            returnValue = false;
        }

        return returnValue;
    }
}

```

Has anyone got any ideas?  Is there a "correct" format to writing an applet which I am not following?  I was assuming that applets would have worked in the same was as writing desktop apps.

Paul

---

### Post by PaulM1985 on 2012-01-22
Bump.

---

### Post by Hetepeperfan on 2012-01-22
I'm by no means a java expert, but in the past I used processing which is a kind of language on top of java, or actually just java. They had their own IDE that could export a program as java application or as java applet.  The only thing I can say is about your assumption:
 > I was assuming that applets would have worked in the same was as writing desktop appsThis is not entirely true. Because once programs start running in a webbrowser, there are way more security issues. People don't like that a java program loads all kind of information down to there computer and excecute it, sometimes javaapplets must be signed in order to download information from a server. But as I started with I'm not really a Java programmer, so unfortunately. I'm not qualified to help you any further.

---

### Post by PaulM1985 on 2012-01-23
> **Hetepeperfan said:**
> This is not entirely true. Because once programs start running in a webbrowser, there are way more security issues.
I know this is the case, I meant to say that I assumed that the user interface and use of Swing would be the same for applets and desktop applications.

Paul

---

