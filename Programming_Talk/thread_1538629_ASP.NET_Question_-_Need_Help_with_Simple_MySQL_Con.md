---
title: "ASP.NET Question - Need Help with Simple MySQL Connection using C#"
date: 2010-07-25
forum: Programming Talk
---

### Post by issachan on 2010-07-25
Hey all, I need help with this. I'm forced to do this project in ASP.NET otherwise I'd have done it in PHP and would have completed this long ago. 

I'm running Ubuntu (yay Ubuntu!) and have been developing this project in MonoDevelop 2.4 and uploading to a Windows server run by GoDaddy.com. 

Now, here's my problem...

I'm creating a shopping cart from scratch. I've created a catalog of  various products and item detail pages which are linked to the database  via a "SqlDataSource" - that part works fine. Now I'm trying to install an add to cart button,  and here's where I'm encountering problems...

In the codebehind of  the page I have the button event set up and working, it changes a label  to say the item has been added. I add a MySQL connection using the  namespace below: 

```
using MySql.Data.MySqlClient;  
using MySql.Data.Types; 
```using MySql.Data.MySqlClient; using MySql.Data.Types;
 Next  I changed the button event code to something similar to the following:

```
public void AddtoCart()
        {
            // Check for cookie
            if(Request.Cookies["mycart"] != null)
            {
                int cartnum = Server.HtmlEncode(Request.Cookies["mycart"]["cartnum"]);
            }
            else // If no cookie is found...
            {
                // Generate random cart number
                int cartnum = Random.next(1000,9999);
                
                // Create new cookie
                Response.Cookies["mycart"]["cartnum"] = cartnum;
                Response.Cookies["mycart"].Expires = DateTime.Now.AddDays(1);
            }
            
            
            // Get Product ID from URL
            int prodID = Request.QueryString("ProductID");
            
            string strProvider = "Server=myserver; Port=1234; Database=mydatabase; Uid=mydatabase; Pwd='password'";
            int qty = MyTextBox.Text;
            
            MySqlConnection mysqlCon = new MySqlConnection(strProvider);
            
            mysqlCon.Open();
            
            string insertSQL = "INSERT INTO ShoppingCart (cartnum, productid, qty) VALUES('" + cartnum + ", " + prodID + ", " + qty + "')";
            
            MySqlCommand mysqlCmd = new MySqlCommand(insertSQL,mysqlCon);
            
        }
```When I build it, it says that it can't locate the mysql namespaces  and gives me an CS0246 error four times. The files to which it is  referring are in the bin folder of the project (and in the root bin folder) and I have the files  linked to the project via the web.config file. 

I thought maybe it  just needs to be uploaded, but when I upload the files as is, the  button doesn't do anything - the button will make the label display  whatever was in the last successful build.

I don't know what I'm doing wrong, any ideas?

The Microsoft community has not been helpful with this (not surprising, I know) and I've searched the web for a solution but to no avail. 

I need to finish this project today, if possible, but at this rate it'll be 10 years and a few centuries because I'm about ready to throw the thing out the window and be done with it!

Please help me! It's driving me crazy!! :(

---

### Post by issachan on 2010-07-25
If I can't get the page to connect to the database, can I call upon the existing connection that was made via the web.config file? 

The following is the connection string in the web.config file:

```
<connectionStrings>
        <add name="sqlDataMaster" connectionString="server=myserver;User Id=myusername;password=mypassword;database=mydatabase"
            providerName="MySql.Data.MySqlClient" />
      </connectionStrings>
```In the .aspx file I successful link a datalist to the database with the following code:

```

<asp:SqlDataSource ID="SqlDataSource1" runat="server"
    ConnectionString="<%$ ConnectionStrings:sqlDataMaster %>"
    ProviderName="<%$ ConnectionStrings:sqlDataMaster.ProviderName %>"
    SelectCommand="SELECT * FROM Products WHERE (Products.productid = @productid)">
        <SelectParameters>
            <asp:QueryStringParameter Name="productID" QueryStringField="ProductID" Type="Int32" />
        </SelectParameters>
</asp:SqlDataSource>
```**Could I call the working MySQL connection using it's name "sqlDataMaster" as I did in the code above? If so, how do I go about it?**

---

### Post by issachan on 2010-07-25
I hate Microsoft!!! I'm fed up with this project and I'm fed up using ASP.NET!!

I'm turning my project into a **HYBRID**! A hybrid of ASP.NET and PHP - PHP will handle everything that ASP.NET seems to have issues with.. which is like practically everything. 

If my professor doesn't like it, too bad. At least it will work and it will work properly!

While my project is currently incomplete, you can watch me update it and get everything working properly as the day goes on. 

[http://melissasdomain.com/homework5/Default.aspx](http://melissasdomain.com/homework5/Default.aspx)

I swear there needs to be something done in regards to Microsoft's dominance in colleges and universities... *sigh*

Anyway, wish me luck!

---

### Post by PaulM1985 on 2010-07-26
Did you import your mysql dll files as references into your project?

I think you can right click on References then select dlls that you want to add.

Paul

---

