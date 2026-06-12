---
title: "LemonPOS / C++"
date: 2009-09-03
forum: Programming Talk
---

### Post by memyself on 2009-09-03
Hy,

I need some help with lemonPOS "persa" and the c++ source.

LINK: [http://sourceforge.net/apps/mediawiki/lemonpos/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/lemonpos/index.php?title=Main_Page)
Source: [http://sourceforge.net/projects/lemonpos/files/lemonpos/persa/lemonpos-persa-0.8.tar.bz2/download](http://sourceforge.net/projects/lemonpos/files/lemonpos/persa/lemonpos-persa-0.8.tar.bz2/download)

In the "producteditor.cpp" file (persa/squeeze/src) the finalprice is calculatet.
I need to get the utility calculated not the final price.
Something like "utility = finalPrice - tax - tax2 - cost;"
So that I put in cost, tax and final price and can see what the utility is.

Can somebody please tell me where and how to change source to get this working.

Thanks for your help!

---

### Post by j7%&lt;RmUg on 2009-09-03
Just try experimenting with it, thats what programming is all about. Im also not going to help you if this is homework.

---

### Post by memyself on 2009-09-03
I tryed experimenting with it! Always got error messages. I never learned c++! And no,  its no homework.
This didn't make errors but don't work as I wanted:

void ProductEditor::calculatePrice()
{
 double finalPrice=0.0;
 if (ui->editCost->text().isEmpty()) {
   ui->editCost->setFocus();
 }
 else if (ui->editUtility->text().isEmpty()) {
   ui->editUtility->setFocus();
 }
 else if (ui->editTax->text().isEmpty()) {
   ui->editTax->setText("0.0");
   ui->editTax->setFocus();
   ui->editTax->selectAll();
 }
 else {
  if (ui->editExtraTaxes->text().isEmpty()) {
   ui->editExtraTaxes->setText("0.0");
   ui->editExtraTaxes->setFocus();
   ui->editExtraTaxes->selectAll();
  }
  //TODO: if TAXes are included in cost...
  double cost    = ui->editCost->text().toDouble();
  double utility = ui->editUtility->text().toDouble();
  double tax     = ui->editTax->text().toDouble();
  double tax2    = ui->editExtraTaxes->text().toDouble();
  //Utility is calculated before taxes... Taxes include utility... is it ok?
  utility = ((utility/100)*(finalPrice - cost - tax));
  double cu      = cost;
  tax     = ((tax/100)*cu);
  tax2    = ((tax2/100)*cu);
  utility = finalPrice - tax - cost;
  
  // BFB: avoid more than 2 decimal digits in finalPrice. Round.
  ui->editFinalPrice->setText(QString::number(finalPrice,'f',2));
  ui->editFinalPrice->selectAll();
  ui->editFinalPrice->setFocus();
  }
}

**********************
This is the original source:

void ProductEditor::calculatePrice()
{
 double finalPrice=0.0;
 if (ui->editCost->text().isEmpty()) {
   ui->editCost->setFocus();
 }
 else if (ui->editUtility->text().isEmpty()) {
   ui->editUtility->setFocus();
 }
 else if (ui->editTax->text().isEmpty()) {
   ui->editTax->setText("0.0");
   ui->editTax->setFocus();
   ui->editTax->selectAll();
 }
 else {
  if (ui->editExtraTaxes->text().isEmpty()) {
   ui->editExtraTaxes->setText("0.0");
   ui->editExtraTaxes->setFocus();
   ui->editExtraTaxes->selectAll();
  }
  //TODO: if TAXes are included in cost...
  double cost    = ui->editCost->text().toDouble();
  double utility = ui->editUtility->text().toDouble();
  double tax     = ui->editTax->text().toDouble();
  double tax2    = ui->editExtraTaxes->text().toDouble();
  //Utility is calculated before taxes... Taxes include utility... is it ok?
  utility = ((utility/100)*cost);
  double cu      = cost + utility;
  tax     = ((tax/100)*cu);
  tax2    = ((tax2/100)*cu);
  finalPrice = cost + utility + tax + tax2;
  
  // BFB: avoid more than 2 decimal digits in finalPrice. Round.
  ui->editFinalPrice->setText(QString::number(finalPrice,'f',2));
  ui->editFinalPrice->selectAll();
  ui->editFinalPrice->setFocus();
  }
}

Some tip?

---

### Post by TGArcher on 2010-03-12
Yeah. a good tip is use code tags. they look like this:

```

some code here

```

then we might be able to help out a little better.

---

