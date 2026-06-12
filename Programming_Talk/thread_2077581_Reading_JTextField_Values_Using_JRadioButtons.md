---
title: "Reading JTextField Values Using JRadioButtons"
date: 2012-10-28
forum: Programming Talk
---

### Post by kevinharper on 2012-10-28
This is a tip calculator:
```
import java.awt.BorderLayout;
import java.awt.Dimension;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.BoxLayout;
import javax.swing.ButtonGroup;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JRadioButton;
import javax.swing.JTextField;


public class CalculateForm extends JFrame {
	private JPanel formLayout;
	
	private int W_WIDTH = 250,
				W_HEIGHT = 270;
	
	private int PNLFIELD_WIDTH  = W_WIDTH - 10;
	
	private int TXTFIELD_WIDTH  = 100;
	private int TXTFIELD_HEIGHT = 18;
	
	private JPanel pnlBilledAmount;
	private JLabel lblBilledAmount; 
	private JTextField txtBilledAmount;
	private float billedAmount;
	
	private float DEFAULT_TAX_RATE = 9.1f;
	private JPanel pnlTaxRate, pnlTaxRateDefault, pnlTaxRateUseOther;
	private JRadioButton rbtnTaxRateDefault, rbtnTaxRateUseOther;
	private ButtonGroup taxRBTNs;
	private JLabel lblTaxRate, lblTaxRateDefaultPercentage;
	private JTextField txtTaxRateUseOther;
	private float taxRate = DEFAULT_TAX_RATE;
	
	private JPanel pnlTipAmount, pnlTipAmountPercent, pnlTipAmountDollars;
	private JRadioButton rbtnTipAmountPercent, rbtnTipAmountDollars;
	private ButtonGroup tipRBTNs;
	private JLabel lblTipAmount;
	private JTextField txtTipAmountPercent, txtTipAmountDollars;
	private float tipAmount;
	
	private JPanel pnlCalculate;
	private JButton btnCalculate;
	
	private JPanel pnlTotalAmount;
	private JLabel lblTotalAmount;
	
	private JPanel pnlSplit;
	private JButton btnSplitBill;
	
	private float totalOwed = 0;
	
	CalculateForm(){
		//Window Parameters
		this.setTitle("Restaurant Bill Split Assitant");
		this.setSize(W_WIDTH, W_HEIGHT);
		this.setResizable(false);
		this.setDefaultCloseOperation(EXIT_ON_CLOSE);
		
		//Instantiate Billed Amount Components
		pnlBilledAmount = new JPanel();
		pnlBilledAmount.setSize(new Dimension(PNLFIELD_WIDTH, 30));
		pnlBilledAmount.setLayout(new BorderLayout());
		lblBilledAmount = new JLabel();
		txtBilledAmount = new JTextField();
		
		lblBilledAmount.setText("Billed Amount: ");
		txtBilledAmount.setPreferredSize(new Dimension(TXTFIELD_WIDTH, TXTFIELD_HEIGHT));
		txtBilledAmount.setHorizontalAlignment(JTextField.RIGHT);
		
		//Instantiate Tax Rate Components
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
		
		//Instantiate Tip Amount Components
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
		
		//Instantiate Calculate Button, Total Amount Label, & Split Button
		pnlCalculate = new JPanel();
		pnlCalculate.setPreferredSize(new Dimension(PNLFIELD_WIDTH, 30));
		btnCalculate = new JButton();
		btnCalculate.setText("Calculate");
		btnCalculate.addActionListener(new actionPerformed());
		
		pnlTotalAmount = new JPanel();
		lblTotalAmount = new JLabel();
		
		lblTotalAmount.setText("Total Amount Due: ");
		
		pnlSplit 	 = new JPanel();
		btnSplitBill = new JButton();
		
		//Display Components
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
	
	private class actionPerformed implements ActionListener{
		@Override
	    public void actionPerformed(ActionEvent ae){
			if(ae.getSource() == btnCalculate){
				try{
					billedAmount = Float.parseFloat(txtBilledAmount.getText());
					System.out.println("billedAmount: " + billedAmount);
					System.out.println("taxRate: " + taxRate);
					System.out.println("tipAmount: " + tipAmount);
					
					Calculate c = new Calculate(billedAmount, taxRate, tipAmount);
					
					lblTotalAmount.setText("Total Amount Due: " + c.getTotalOwed());
				}
				finally{
					System.out.println("Error.");
				}
			}
			else if(ae.getSource() == rbtnTaxRateDefault){
				taxRate = DEFAULT_TAX_RATE;
			}
			else if(ae.getSource() == rbtnTaxRateUseOther){
				taxRate = Float.parseFloat(txtTaxRateUseOther.getText());
			}
			else if(ae.getSource() == rbtnTipAmountPercent){
				tipAmount = Float.parseFloat(txtTipAmountPercent.getText());
			}
			else if(ae.getSource() == rbtnTipAmountDollars){
				tipAmount = Float.parseFloat(txtTipAmountDollars.getText());
			}
			
		}
	}
}
```

UI looks fugly, yes. But I'll deal with that later - once I get everything else working.

At the moment I'm unable to assign the values corresponding to the selected radio buttons. taxRate, for example, is always equal to 9.1 and tipAmount is 0.

I was told once to group depending on function and not type.

---

### Post by kevinharper on 2012-10-28
In case you need to see the Calculate class:

```
public class Calculate {
	private float billedAmount;
	private float totalTax;
	private float totalTip;
	private float totalOwed;
	
	Calculate(float bld, float tax, float tip){
		billedAmount = bld;
		totalTax = tax;
		totalTip = tip;
	}
	
	public float getTotalOwed(){
		totalOwed = billedAmount + totalTax + totalTip;
		
		return totalOwed;
	}
}
```

---

### Post by spjackson on 2012-10-29
> 
At the moment I'm unable to assign the values corresponding to the selected radio buttons. taxRate, for example, is always equal to 9.1 and tipAmount is 0.

My Java knowledge is limited, but here goes.

actionPerformed isn't being added as a listener for your radio buttons, so your code to change these values is never called. You need to call addActionListener for each of your radio buttons.

Some more observations:
[LIST=1]
[*]As a user, I expect to click the radio button then type the value in the next field. Your code is designed so that the user has to fill the value in first, then click the radio button, because you read the value only when the radio button is clicked.

[*]You are not calculating any percentages: you always treat values as amounts.

[*]You are not handling exceptions from parsing floats - I'm not sure whether you want to.
[/LIST]

---

### Post by kevinharper on 2012-10-29
THANK YOU! I agree!

Will try it out this evening and will let you know how it goes! But yes, I am pretty sure that's it.

---

### Post by kevinharper on 2012-10-31
Okay... So not exactly.

What I did was, when "Calculate" button was pressed, checked to see which ratio buttons were selected. I would read text field info depending on selected radio buttons.

---

