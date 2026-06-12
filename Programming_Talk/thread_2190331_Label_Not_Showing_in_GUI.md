---
title: "Label Not Showing in GUI"
date: 2013-11-26
forum: Programming Talk
---

### Post by WP6r8PA on 2013-11-26
```
import java.awt.BorderLayout;import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPanel;
import javax.swing.JTextField;


public class AccountFrame extends JFrame {
    private static final int FRAME_WIDTH = 900;
    private static final int FRAME_HEIGHT = 200;
    


    private static final double INITIAL_BALANCE = 0;
    
    private JLabel depositLabel;
    private JLabel withdrawLabel;
    private JTextField depositField;
    private JTextField withdrawField;
    private JButton depositbutton;
    private JButton withdrawButton;
    private JLabel balanceLabel;
    
    private double balance;
    
    public AccountFrame()
    {
        balance = INITIAL_BALANCE;
        balanceLabel = new JLabel("Balance: " + balance);
        createTextFields();
        createButtons();
        createPanel();
        setSize(FRAME_WIDTH, FRAME_HEIGHT);
    }
    
    private void createTextFields()
    {
        depositLabel = new JLabel("Deposit: ");
        withdrawLabel = new JLabel("Withdraw: ");
        balanceLabel = new JLabel("Balance: " + balance);
        final int FIELD_WIDTH = 2;
        depositField = new JTextField(FIELD_WIDTH);
        withdrawField = new JTextField(FIELD_WIDTH);
        depositField.setText("" + balance);
    }
    
    /**
    Adds funds to the balance and updates the display.
    */
    class AddDepositListener implements ActionListener
    {
        public void actionPerformed(ActionEvent event)
        {
            double deposit = Double.parseDouble(depositField.getText());
            balance = balance + deposit;
            balanceLabel.setText("Balance: " + balance);
        }
    }
    
    class AddWithdrawListener implements ActionListener
    {
        public void actionPerformed(ActionEvent event)
        {
            double withdraw = Double.parseDouble(withdrawField.getText());
            balance = balance - withdraw;
            balanceLabel.setText("Balance: " + balance);
        }
    }
    
    private void createButtons()
    {
        depositbutton = new JButton("Add Funds");
        withdrawButton = new JButton("Withdraw Funds");
        ActionListener dlistener = new AddDepositListener();
        ActionListener wlistener = new AddWithdrawListener();
        depositbutton.addActionListener(dlistener);
        withdrawButton.addActionListener(wlistener);
    }
    
    private void createPanel()
    {
        JPanel panel = new JPanel();
        panel.setLayout(new BorderLayout());
        JPanel buttonPanel = new JPanel();
        buttonPanel.setLayout(new GridLayout(4, 2));
        buttonPanel.add(depositLabel);
        buttonPanel.add(withdrawLabel);
        buttonPanel.add(depositField);
        buttonPanel.add(withdrawField);
        buttonPanel.add(depositbutton);
        buttonPanel.add(withdrawButton);
        buttonPanel.add(balanceLabel);
        panel.add(buttonPanel, BorderLayout.CENTER);
        panel.add(balanceLabel);
        add(panel);
        add(buttonPanel);
    }
}

```

```
import javax.swing.JFrame;/**
This program acts as a bank account.
*/
public class AccountViewer {
    public static void main(String[] args) {
        JFrame frame = new AccountFrame();
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setVisible(true);
    }
}
```

There should be a text: "Balance: " on the bottom that shows the changes in the account balance. It was there before I organized the layout in grid style!! Why when adding the grid style did it disappear? How do I get it to reappear? You can see I tried adding it in multiple different ways and it's STILL not showing up.

---

### Post by WP6r8PA on 2013-11-27
Found my own solution by removing[FONT=Ubuntu Mono, monospace][COLOR=#000000] [/COLOR][/FONT][COLOR=#000000][FONT=Ubuntu Mono]panel.add(balanceLabel);[/FONT][/COLOR]

---

