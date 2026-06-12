---
title: "Simple Tip Calculator (Java)"
date: 2012-10-31
forum: Programming Talk
---

### Post by kevinharper on 2012-10-31
I have the following three classes:

StartProgram.java:
```

public class StartProgram {
	public static void main(String[] args) {
		CalculateForm w = new CalculateForm();
		w.setVisible(true);
	}

}
```

CalculatorForm.java:
```
import java.awt.BorderLayout;
import java.awt.Color;
import java.awt.Dimension;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.BoxLayout;
import javax.swing.ButtonGroup;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JPanel;
import javax.swing.JRadioButton;
import javax.swing.JTextField;


public class CalculateForm extends JFrame {
	//Constants
	private int W_WIDTH = 250,
				W_HEIGHT = 270;	
	private int PNLFIELD_WIDTH  = W_WIDTH - 10;	
	private int TXTFIELD_WIDTH  = 100;
	private int TXTFIELD_HEIGHT = 18;	
	private float DEFAULT_TAX_RATE = 9.1f;
	
	//Variables
	private float billedAmount   = 0;
	private float taxRate        = 0;
	private float totalOwed      = 0;
	private float tipRate        = 0;
	private float tipAmount      = 0;
	private int   numGuests      = 0;
	private float amountPerGuest = 0;
	
	//Form Elements
	private JPanel formLayout;
	
	//Form Elements: Billed Amount
	private JPanel pnlBilledAmount;
	private JLabel lblBilledAmount; 
	private JTextField txtBilledAmount;
	
	//Form Elements: Tax Rate
	private JPanel pnlTaxRate, pnlTaxRateDefault, pnlTaxRateUseOther;
	private JRadioButton rbtnTaxRateDefault, rbtnTaxRateUseOther;
	private ButtonGroup taxRBTNs;
	private JLabel lblTaxRate, lblTaxRateDefaultPercentage;
	private JTextField txtTaxRateUseOther;
	
	//Form Elements: Tip Amount
	private JPanel pnlTipAmount, pnlTipAmountPercent, pnlTipAmountDollars;
	private JRadioButton rbtnTipAmountPercent, rbtnTipAmountDollars;
	private ButtonGroup tipRBTNs;
	private JLabel lblTipAmount;
	private JTextField txtTipAmountPercent, txtTipAmountDollars;
	
	//Form Elements: Calculate Button, Total Amount, Split Button
	private JPanel pnlCalculate;
	private JButton btnCalculate;
	
	private JPanel pnlTotalAmount;
	private JLabel lblTotalAmount;
	
	private JPanel pnlSplit;
	private JButton btnSplitBill;
	
	//Start Form
	CalculateForm(){
		//Window Parameters
		this.setTitle("Restaurant Bill Split Assitant");
		this.setSize(W_WIDTH, W_HEIGHT);
		this.setResizable(false);
		this.setDefaultCloseOperation(EXIT_ON_CLOSE);
		
		//Instantiate Billed Amount Elements
		pnlBilledAmount = new JPanel();
		pnlBilledAmount.setSize(new Dimension(PNLFIELD_WIDTH, 30));
		pnlBilledAmount.setLayout(new BorderLayout());
		lblBilledAmount = new JLabel();
		txtBilledAmount = new JTextField();
		
		lblBilledAmount.setText("Billed Amount: ");
		txtBilledAmount.setPreferredSize(new Dimension(TXTFIELD_WIDTH, TXTFIELD_HEIGHT));
		txtBilledAmount.setHorizontalAlignment(JTextField.RIGHT);
		
		//Instantiate Tax Rate Elements
		pnlTaxRate 		   = new JPanel();
		pnlTaxRate.setPreferredSize(new Dimension(PNLFIELD_WIDTH, 30));
		pnlTaxRate.setLayout(new BorderLayout());
		pnlTaxRateDefault  = new JPanel();
		pnlTaxRateDefault.setLayout(new BorderLayout());
		pnlTaxRateUseOther = new JPanel();
		pnlTaxRateUseOther.setLayout(new BorderLayout());		
		rbtnTaxRateDefault  = new JRadioButton();
		rbtnTaxRateUseOther = new JRadioButton();
		taxRBTNs = new ButtonGroup();
		lblTaxRate 					= new JLabel();
		lblTaxRateDefaultPercentage = new JLabel();
		txtTaxRateUseOther = new JTextField();
		
		taxRBTNs.add(rbtnTaxRateDefault);
		taxRBTNs.add(rbtnTaxRateUseOther);
		taxRBTNs.setSelected(rbtnTaxRateDefault.getModel(), true);
		rbtnTaxRateDefault.setText("Default Tax Rate: ");
		rbtnTaxRateUseOther.setText("Use Another Tax Rate: ");
		lblTaxRate.setText("Tax Rate: ");
		lblTaxRateDefaultPercentage.setText("" + DEFAULT_TAX_RATE);
		txtTaxRateUseOther.setPreferredSize(new Dimension(TXTFIELD_WIDTH, TXTFIELD_HEIGHT));
		txtTaxRateUseOther.setHorizontalAlignment(JTextField.RIGHT);
		
		//Instantiate Tip Amount Elements
		pnlTipAmount = new JPanel();
		pnlTipAmount.setPreferredSize(new Dimension(PNLFIELD_WIDTH, 30));
		pnlTipAmount.setLayout(new BorderLayout());
		pnlTipAmountPercent = new JPanel();
		pnlTipAmountPercent.setLayout(new BorderLayout());
		pnlTipAmountDollars = new JPanel();
		pnlTipAmountDollars.setLayout(new BorderLayout());
		rbtnTipAmountPercent = new JRadioButton();
		rbtnTipAmountDollars = new JRadioButton();
		tipRBTNs = new ButtonGroup();
		lblTipAmount 		= new JLabel();
		txtTipAmountPercent = new JTextField();
		txtTipAmountDollars = new JTextField();
		
		tipRBTNs.add(rbtnTipAmountPercent);
		tipRBTNs.add(rbtnTipAmountDollars);
		rbtnTipAmountPercent.setText("Percentage: ");
		rbtnTipAmountDollars.setText("Dollars: ");
		lblTipAmount.setText("Tip Amount: ");
		txtTipAmountPercent.setPreferredSize(new Dimension(TXTFIELD_WIDTH, TXTFIELD_HEIGHT));
		txtTipAmountPercent.setHorizontalAlignment(JTextField.RIGHT);
		txtTipAmountDollars.setPreferredSize(new Dimension(TXTFIELD_WIDTH, TXTFIELD_HEIGHT));
		txtTipAmountDollars.setHorizontalAlignment(JTextField.RIGHT);
		
		//Instantiate Calculate Button, Total Amount Label,
		//	& Split Button
		pnlCalculate = new JPanel();
		pnlCalculate.setPreferredSize(new Dimension(PNLFIELD_WIDTH, 30));
		btnCalculate = new JButton();
		btnCalculate.setText("Calculate");
		btnCalculate.addActionListener(new actionPerformed());
		
		pnlTotalAmount = new JPanel();
		lblTotalAmount = new JLabel();
		
		lblTotalAmount.setText("Total Amount Due: ");
		
		pnlSplit 	 = new JPanel();
		pnlCalculate.setPreferredSize(new Dimension(PNLFIELD_WIDTH, 30));
		btnSplitBill = new JButton();
		btnSplitBill.setText("Split Bill");
		btnSplitBill.addActionListener(new actionPerformed());
		
		//Display Elements
		formLayout = new JPanel();
		
		formLayout.setLayout(new BoxLayout(formLayout, BoxLayout.Y_AXIS));
		
		pnlBilledAmount.add(lblBilledAmount, BorderLayout.WEST);
		pnlBilledAmount.add(txtBilledAmount, BorderLayout.EAST);
		pnlTaxRate.add(lblTaxRate, BorderLayout.WEST);
		
		pnlTaxRateDefault.add(rbtnTaxRateDefault, BorderLayout.WEST);
		pnlTaxRateDefault.add(lblTaxRateDefaultPercentage, BorderLayout.EAST);
		pnlTaxRateUseOther.add(rbtnTaxRateUseOther, BorderLayout.WEST);
		pnlTaxRateUseOther.add(txtTaxRateUseOther, BorderLayout.EAST);
		
		pnlTipAmount.add(lblTipAmount, BorderLayout.WEST);
		pnlTipAmountPercent.add(rbtnTipAmountPercent, BorderLayout.WEST);
		pnlTipAmountPercent.add(txtTipAmountPercent, BorderLayout.EAST);
		pnlTipAmountDollars.add(rbtnTipAmountDollars, BorderLayout.WEST);
		pnlTipAmountDollars.add(txtTipAmountDollars, BorderLayout.EAST);
		
		pnlCalculate.add(btnCalculate);
		pnlTotalAmount.add(lblTotalAmount);
		pnlSplit.add(btnSplitBill);
		
		formLayout.add(pnlBilledAmount);
		formLayout.add(pnlTaxRate);
		formLayout.add(pnlTaxRateDefault);
		formLayout.add(pnlTaxRateUseOther);
		formLayout.add(pnlTipAmount);
		formLayout.add(pnlTipAmountPercent);
		formLayout.add(pnlTipAmountDollars);
		formLayout.add(pnlCalculate);
		formLayout.add(pnlTotalAmount);
		formLayout.add(pnlSplit);
		
		this.add(formLayout);
	}
	
	//Do when "Calculate" or "Split Bill" buttons pressed
	private class actionPerformed implements ActionListener{
		private boolean validInput = false;
		
		@Override
	    public void actionPerformed(ActionEvent ae){
			//Do when "Calculate" button pressed
			if(ae.getSource() == btnCalculate){
				//Get & verify values. Color bg red if input is incorrect
				try{
					txtBilledAmount.setBackground(Color.WHITE);
					billedAmount = Float.parseFloat(txtBilledAmount.getText());
					validInput = true;
				}
				catch(Exception e){
					txtBilledAmount.setBackground(Color.RED);
					validInput = false;
				}
				
				try{
					txtTaxRateUseOther.setBackground(Color.WHITE);
					if(rbtnTaxRateDefault.isSelected() == true)
						taxRate = DEFAULT_TAX_RATE;
					else {
						taxRate = Float.parseFloat(txtTaxRateUseOther.getText());
					}
					
					validInput = true;
				}
				catch(Exception e){
					txtTaxRateUseOther.setBackground(Color.RED);
					validInput = false;
				}
				
				try{
					txtTipAmountPercent.setBackground(Color.WHITE);
					txtTipAmountDollars.setBackground(Color.WHITE);
					if(rbtnTipAmountPercent.isSelected() == true){
						tipRate = Float.parseFloat(txtTipAmountPercent.getText());
						validInput = true;
					}
					else if (rbtnTipAmountDollars.isSelected() == true){
						tipAmount = Float.parseFloat(txtTipAmountDollars.getText());
						validInput = true;
					}
					else{
						throw new Exception("No Tip Amount Entered.");
					}
						
				}
				catch(Exception e){
					txtTipAmountPercent.setBackground(Color.RED);
					txtTipAmountDollars.setBackground(Color.RED);
					tipRate   = 0;
					tipAmount = 0;
					validInput = false;
				}
				
				//Only create Calculate object if all input is valid
				if(validInput == true){
					Calculate c = new Calculate(billedAmount, taxRate, tipRate, tipAmount);
					
					totalOwed = c.getTotalOwed();
					lblTotalAmount.setText("Total Amount Due: " + totalOwed);
				}
			}

			//Do if "Split Bill" button is pressed
			else if(ae.getSource() == btnSplitBill){
				numGuests = Integer.parseInt(JOptionPane.showInputDialog(
	                    null,
	                    "Enter number of guests with which to slip the bill.",
	                    "Number of Guests",
	                    1));
				
				System.out.println("Total Amount Due: " + totalOwed + "\n");
				System.out.println("Number of Guests: " + numGuests + "\n");
				amountPerGuest = c.getAmountPerGuest;
				System.out.println("Amount Due per Guest: " + amountPerGuest);
			}
		}
	}
}
```

Calculate.java
```

public class Calculate {
	private float billedAmount;
	private float taxRate;
	private float taxTotal;
	private float tipRate;
	private float tipAmount;
	private float totalOwed;
	private int   numberOfGuests;
	private float amountPerGuest;
	
	Calculate(float bld, float txRt, float tpRt, float tpTtl){
		billedAmount = bld;
		taxRate = txRt/100;
		tipRate = tpRt/100;
		tipAmount = tpTtl;
		numberOfGuests = 1;
		amountPerGuest = 0f;
		
		taxTotal = billedAmount * taxRate;
		if(tipAmount == 0)
			tipAmount = (billedAmount + taxTotal) * tipRate;
	}
	
	public void setNumberOfGuests(int numgsts){
		numberOfGuests = numgsts;
	}
	
	public float getTotalOwed(){
		totalOwed = billedAmount + taxTotal + tipAmount;
		
		return totalOwed;
	}
	
	public float getAmountPerGuest(){
		amountPerGuest = totalOwed / numberOfGuests;
		
		return amountPerGuest;
	}
}
```

I am getting an error inside CalculateForm.java (line 271; second to last statement in class):
```
amountPerGuest = c.getAmountPerGuest;
```
Eclipse says that c is not a variable. Is it because c is instantiated in another section of the if-else-if?

While I'm asking, why am I getting a warning on:
```
public void actionPerformed(ActionEvent ae){
```
and on:
```
public class CalculateForm extends JFrame {
```

---

### Post by tornadof3 on 2012-11-01
I'm pretty sure it is because you instantiate c inside the previous if block. Might it be better to include a

```
private Calculate c;
```

declaration at the very top and instantiate c somewhere else sensible in the program - inside the CalculateForm constructor? However, perhaps it would be good to instantiate c with a blank constructor, and then have some method to set billedAmount, taxRate, tipRate, tipAmount just before you use c.

As to your other errors on actionPerformed etc, what errors do you see?

---

### Post by dazman19 on 2012-11-01
in addition just a personal tip.

Personally I wouldn't call a variable "c" and i wouldnt call a function x. I see you have named the functions well, but i would consider naming the variables something more descriptive about what they are.

Technically there is nothing wrong with using a variable like x, y, z , c, a ... 
However they generally do not help describe what they are.

It may seem like more work, but calling a variable what is actually is makes your coding 10x easier because you dont have these "Scope" problems.

If i look at a massive block of code, and 1/2 way down there is a declaration for "c" and an instansiation to an object, then somewhere towards the bottom you write c.x() then unless i know what c is, it makes is harder for me to read the code. 

I do like he they way you have named most of your functions, however I prefer to make a variable called listOfChickens rather than calling it x.

---

### Post by spjackson on 2012-11-01
> **kevinharper said:**
> 
I am getting an error inside CalculateForm.java (line 271; second to last statement in class):
```
amountPerGuest = c.getAmountPerGuest;
```
Eclipse says that c is not a variable. Is it because c is instantiated in another section of the if-else-if?

Yes, c is out of scope at that point. You need to restructure your code (or your user interface) because you want to perform exactly the same form validation and calculation whichever of the 2 buttons is pressed, but if it's btnSplitBill then you have some extra work to do.

> 
While I'm asking, why am I getting a warning on:
```
public void actionPerformed(ActionEvent ae){
```
and on:
```
public class CalculateForm extends JFrame {
```

It would have helped if you told us what the warnings were. I have loaded your code into eclipse so I know that the first case is "This method has a constructor name". The ActionListener interface has a method actionPerformed which you are correctly overriding. However, your class is also called actionPerformed. This is a bad idea: rename your class. (It is a convention in Java for class names to begin with an uppercase letter.)

The second concerns serialization because JFrame is serializable. Either ignore the warning or use one of the Quick Fix methods in eclipse to sort it out.

---

### Post by kevinharper on 2012-11-01
Awesome guys. Thank you! Will try these out later tonight or tomorrow evening and will confirm "solved" or reply with more questions/errors that come up from the changes.

---

### Post by kevinharper on 2012-11-01
I just remembered why I had split this up into if-then.

```
if(ae.getSource() == btnCalculate){
				//Get & verify values. Color bg red if input is incorrect
				try{
					txtBilledAmount.setBackground(Color.WHITE);
					billedAmount = Float.parseFloat(txtBilledAmount.getText());
					validInput = true;
				}
				catch(Exception e){
					txtBilledAmount.setBackground(Color.RED);
					validInput = false;
				}
				
				try{
					txtTaxRateUseOther.setBackground(Color.WHITE);
					if(rbtnTaxRateDefault.isSelected() == true)
						taxRate = DEFAULT_TAX_RATE;
					else {
						taxRate = Float.parseFloat(txtTaxRateUseOther.getText());
					}
					
					validInput = true;
				}
				catch(Exception e){
					txtTaxRateUseOther.setBackground(Color.RED);
					validInput = false;
				}
				
				try{
					txtTipAmountPercent.setBackground(Color.WHITE);
					txtTipAmountDollars.setBackground(Color.WHITE);
					if(rbtnTipAmountPercent.isSelected() == true){
						tipRate = Float.parseFloat(txtTipAmountPercent.getText());
						validInput = true;
					}
					else if (rbtnTipAmountDollars.isSelected() == true){
						tipAmount = Float.parseFloat(txtTipAmountDollars.getText());
						validInput = true;
					}
					else{
						throw new Exception("No Tip Amount Entered.");
					}
						
				}
				catch(Exception e){
					txtTipAmountPercent.setBackground(Color.RED);
					txtTipAmountDollars.setBackground(Color.RED);
					tipRate   = 0;
					tipAmount = 0;
					validInput = false;
				}
				
				//Only create Calculate object if all input is valid
				if(validInput == true){
					Calculate c = new Calculate(billedAmount, taxRate, tipRate, tipAmount);
					
					totalOwed = c.getTotalOwed();
					lblTotalAmount.setText("Total Amount Due: " + totalOwed);
				}
			}
```
I only want to create a Calculate object if validInput == true. Does anyone have a better suggested than what I did (nesting the declaration inside an if-then statement)?

---

### Post by muteXe on 2012-11-02
Just have one massive try/catch block around the whole thing?
Although that's still pretty ugly.  It doesn't feel right to me to set variables in catch blocks in the what that you have. Exceptions should be there to handle *exceptional* cases.

---

### Post by kevinharper on 2012-11-02
I agree. I got some ideas in last night's lecture about how to clean this up.  Going to add some methods in there somewhere. Thanks guys. Will post corrected code later.

---

