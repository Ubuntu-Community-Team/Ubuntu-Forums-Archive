---
title: "Help with Java networking"
date: 2009-11-28
forum: Programming Talk
---

### Post by Yes on 2009-11-28
I'm making a networked tic-tac-toe game and I'm having some trouble.  It seems to either not read from or send to the other program correctly, but the program still continues like normal.  That is, when you press a button in one program nothing happens in the other program while everything else behaves normally.  Can anyone take a quick look at my code and help me out?

Thanks!

TicTacToeServer:

[php]import java.net.*;
import java.io.*;

public class TicTacToeServer {

	static final String HANDSHAKE = "Iamme";
	
	public static void main (String args[]) {
		boolean won;
		
		TicTacToeGUI window = new TicTacToeGUI ();
		window.setTitle ("Tic Tac Toe Server");
		window.letter = "O";
				
		ServerSocket listener;
		Socket connection;
		BufferedReader incoming;
		BufferedReader userInput = new BufferedReader (new InputStreamReader (System.in));
		String messageIn;
		PrintWriter outgoing;
		String messageOut;
		
		try {
			listener = new ServerSocket (8080); //create server socket
			System.out.println ("Listening on port 8080");
			
			connection = listener.accept (); //listen and accept incoming connection
			listener.close ();
			
			incoming = new BufferedReader (new InputStreamReader (connection.getInputStream ())); //creat input/output streams
			outgoing = new PrintWriter (connection.getOutputStream ());
			
			outgoing.println (HANDSHAKE); //send handshake
			outgoing.flush ();
			
			messageIn = incoming.readLine (); //receive and verify handshake
			if (!messageIn.equals (HANDSHAKE))
				throw new IOException ("Connected client not client");
			
			System.out.println ("Connected to " + connection.getInetAddress () + "."); //print grettings
			outgoing.flush ();
			
		} catch (Exception exc) {
			System.out.println ("Error opening connection: " + exc);
			return;
		}
		
		try {
			while (true) {
				messageIn = incoming.readLine ();
				
				if (messageIn.equals ("1"))
					window.one.setText ("X");
				else if (messageIn.equals ("2"))
					window.two.setText ("X");
				else if (messageIn.equals ("3"))
					window.three.setText ("X");
				else if (messageIn.equals ("4"))
					window.four.setText ("X");
				else if (messageIn.equals ("5"))
					window.five.setText ("X");
				else if (messageIn.equals ("6"))
					window.six.setText ("X");
				else if (messageIn.equals ("7"))
					window.seven.setText ("X");
				else if (messageIn.equals ("8"))
					window.eight.setText ("X");
				else if (messageIn.equals ("9"))
					window.nine.setText ("X");
					
				if (!window.buttonPressed.equals ("-1")) {
					outgoing.println (window.buttonPressed);
					outgoing.flush ();
					window.buttonPressed = "-1";
				}
			}
		} catch (Exception exc) {}
	}	
}[/php]

TicTacToeClient:

[php]import java.net.*;
import java.io.*;

public class TicTacToeClient {
	
	static final String HANDSHAKE = "Iamme";

	public static void main (String args[]) {
		boolean won;
		
		TicTacToeGUI window = new TicTacToeGUI ();
		window.setTitle ("Tic Tac Toe Client");
		window.letter = "X";
		
		Socket connection;
		BufferedReader incoming;
		BufferedReader userInput = new BufferedReader (new InputStreamReader (System.in));
		String messageIn;
		PrintWriter outgoing;
		String messageOut;
	
		try {
			System.out.println ("Connecting to 127.0.0.1 on port 8080");
			connection = new Socket ("127.0.0.1", 8080); //connect to server
			
			incoming = new BufferedReader (new InputStreamReader (connection.getInputStream ())); //create input/output streams
			outgoing = new PrintWriter (connection.getOutputStream ());
			
			outgoing.println (HANDSHAKE); //send handshake
			outgoing.flush ();
			
			messageIn = incoming.readLine (); //receive and verify handshake
			if (!messageIn.equals (HANDSHAKE))
				throw new IOException ("Connected program not server"); 
			
			System.out.println ("Connected"); //print gretting messages
			
		} catch (Exception exc) {
			System.out.println ("Error opening connection: " + exc);
			return;
		}
		
		try {
			while (true) {
				messageIn = incoming.readLine ();
				
				if (messageIn.equals ("1"))
					window.one.setText ("O");
				else if (messageIn.equals ("2"))
					window.two.setText ("O");
				else if (messageIn.equals ("3"))
					window.three.setText ("O");
				else if (messageIn.equals ("4"))
					window.four.setText ("O");
				else if (messageIn.equals ("5"))
					window.five.setText ("O");
				else if (messageIn.equals ("6"))
					window.six.setText ("O");
				else if (messageIn.equals ("7"))
					window.seven.setText ("O");
				else if (messageIn.equals ("8"))
					window.eight.setText ("O");
				else if (messageIn.equals ("9"))
					window.nine.setText ("O");
					
				if (!window.buttonPressed.equals ("-1")) {
					outgoing.println (window.buttonPressed);
					outgoing.flush ();
					window.buttonPressed = "-1";
				}
			}
		} catch (Exception exc) {}	
	}
}[/php]

TicTacToeGUI:

[php]import java.awt.*;
import java.awt.event.*;
import javax.swing.*;


public class TicTacToeGUI extends JFrame {
	
	static JButton one;
	static JButton two;
	static JButton three;
	static JButton four;
	static JButton five;
	static JButton six;
	static JButton seven;
	static JButton eight;
	static JButton nine;
	static String buttonPressed = "-1";
	static String letter;
	
	public TicTacToeGUI () {
		JPanel panel = new Panel ();
		this.setContentPane (panel);
		this.pack ();
		this.setLocation (500, 100);
		this.setDefaultCloseOperation( JFrame.EXIT_ON_CLOSE );
		this.setVisible (true);
	}

	public static class Panel extends JPanel implements ActionListener {
				
		public Panel () {
			
			JPanel buttonPanel = new JPanel ();
			buttonPanel.setLayout (new GridLayout (3,3));
			
			one = new JButton ("1");
			one.addActionListener (this);
			buttonPanel.add (one);
			
			two = new JButton ("2");
			two.addActionListener (this);
			buttonPanel.add (two);
			
			three = new JButton ("3");
			three.addActionListener (this);
			buttonPanel.add (three);
			
			four = new JButton ("4");
			four.addActionListener (this);
			buttonPanel.add (four);
			
			five = new JButton ("5");
			five.addActionListener (this);
			buttonPanel.add (five);
			
			six = new JButton ("6");
			six.addActionListener (this);
			buttonPanel.add (six);
			
			seven = new JButton ("7");
			seven.addActionListener (this);
			buttonPanel.add (seven);
			
			eight = new JButton ("8");
			eight.addActionListener (this);
			buttonPanel.add (eight);
			
			nine = new JButton ("9");
			nine.addActionListener (this);
			buttonPanel.add (nine);
			
			add (buttonPanel);
		}
		
		public void actionPerformed (ActionEvent evt) {
			boolean won;
			
			if (((String)evt.getActionCommand ()).equals ("1")) //check what button was pressed, change that button's state
				one.setText (letter);
			else if (((String)evt.getActionCommand ()).equals ("2"))
				two.setText (letter);
			else if (((String)evt.getActionCommand ()).equals ("3"))
				three.setText (letter);
			else if (((String)evt.getActionCommand ()).equals ("4"))
				four.setText (letter);
			else if (((String)evt.getActionCommand ()).equals ("5"))
				five.setText (letter);
			else if (((String)evt.getActionCommand ()).equals ("6"))
				six.setText (letter);
			else if (((String)evt.getActionCommand ()).equals ("7"))
				seven.setText (letter);
			else if (((String)evt.getActionCommand ()).equals ("8"))
				eight.setText (letter);
			else if (((String)evt.getActionCommand ()).equals ("9"))
				nine.setText (letter);
				
			buttonPressed = (String)evt.getActionCommand ();
			
			won = check ();
			if (won) {
				JOptionPane.showMessageDialog(this, "You Win!");
			}
			
		}
		
		public static boolean check () { //check for a win
		
			if (one.getText().equals (letter) && two.getText().equals (letter) && three.getText().equals (letter))
				return true;
			else if (four.getText().equals (letter) && five.getText().equals (letter) && six.getText().equals (letter))
				return true;
			else if (seven.getText().equals (letter) && eight.getText().equals (letter) && nine.getText().equals (letter))
				return true;
			else if (one.getText().equals (letter) && four.getText().equals (letter) && seven.getText().equals (letter))
				return true;
			else if (two.getText().equals (letter) && five.getText().equals (letter) && eight.getText().equals (letter))
				return true;
			else if (three.getText().equals (letter) && six.getText().equals (letter) && nine.getText().equals (letter))
				return true;
			else if (one.getText().equals (letter) && five.getText().equals (letter) && nine.getText().equals (letter))
				return true;
			else if (three.getText().equals (letter) && five.getText().equals (letter) && seven.getText().equals (letter))
				return true;
		
			return false;
		}
	}
}[/php]

---

### Post by Zugzwang on 2009-11-29
There is a logical problem in your program design.

You should definitely have a look at threading. "while(true)" loops with blocking input should never be executed in the GUI thread of any Java application as it otherwise blocks! Instead, you are better off spawning a second thread for obtaining data from the server and react on it using invokeLater calls. Do some google search for finding out details.

---

### Post by dwhitney67 on 2009-11-29
I re-factored the app (to operate w/o the GUI) to see if there was an issue with the socket, and I found none.

However, I found the original design of the app to be a bit quirky.  I do not see the point of the Server having a GUI element to it.  It should run as a 'black-box'; only the Client should see the GUI.

The Server should maintain the game's state, and report changes to such to the Client, via the socket, thus giving the user the notion that the game is evolving with each input they provide.

IMO, the GUI should be afforded better public interfaces, rather than declaring everything static/public within it.  Overuse of 'static' member data/methods in a class is indicative of a poor design.

Also consider making the Client the action listener, so that when the user clicks on the GUI, the button information can be obtained and forwarded to the Server.

As for the GUI, it is not necessary to declare 9 buttons!  Define an array of buttons, and manage them accordingly.  The GUI should be simple... define the buttons, lay them out, and then provide interfaces so that its buttons can be updated with an 'X' or an 'O'.

Let the Server determine if there is a win situation, not the GUI.  The Server would need to maintain a 3x3 matrix, or 9-cell array, to keep tabs on the state of each space on the game board, and also to disallow the user from clicking on the same cell twice.  Nothing in the code appears to handle this situation.

That's my $0.02 worth of insight.

---

