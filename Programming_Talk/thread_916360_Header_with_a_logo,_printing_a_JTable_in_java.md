---
title: "Header with a logo, printing a JTable in java"
date: 2008-09-10
forum: Programming Talk
---

### Post by azzamite on 2008-09-10
Hi
Does anyone knows how can I personalize the headder that is printed with the method JTable.print(,,,) of java?

I need to add a logo at the top of each page.
[PHP]
|--------|
|--logo--| company name
|--------|

|--col--|--col--|--col--|
.....[/PHP]
But the MessageFormat seems to be text only

---

### Post by azzamite on 2008-09-11
this,complaining(true);
/*
Java is realy good for some things, but sometimes is a real pain in the...
serious, why simple things like this have to be so complicated?
*/
this,complaining(false);

In short, I did this:
1 - Got the code of [TablePrintable.java]("http://www.google.com.mx/search?hl=es&as_qdr=all&q=tableprintable.java&btnG=Buscar&meta="), I couldn't inherit from it (and it wouldn't have been worth of the effort)
2 - Changed the name to ImprimeTabla.java (constructor to)
3 - A draw the logo **after** the header
[PHP]
if (headerText != null) {
    printText(g2d, headerText, hRect, headerFont, imgWidth + 150); //el ancho estimado de la imagen
    //draw the logo here
    g2d.translate(0, headerTextSpace + H_F_SPACE);
}[/PHP]
4 - create the class and print it
[PHP]
//code
ImprimeTabla imp = new ImprimeTabla(this.table, PrintMode.NORMAL, header, footer);
//code
PrinterJob job = PrinterJob.getPrinterJob();
job.setPrintable(imp);
boolean ok = job.printDialog();
if (ok) {
    try {
        job.print();
    } catch (PrinterException ex) {
        /* The job did not successfully complete */
    }
}
[/PHP]

---

