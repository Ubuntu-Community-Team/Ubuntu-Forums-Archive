---
title: "[C++] Boost XML Serialization with Client/Server"
date: 2008-07-31
forum: Programming Talk
---

### Post by dwhitney67 on 2008-07-31
I am experimenting with the C++ XML Serialization Boost library for a simple server application.  Currently the server only permits one client to connect (via TCP socket) at a time; later I will expand this.

Does anyone have any experience with sending XML over TCP?  What is the best way to buffer the data on the server side as it is sent, and how can I determine that a complete XML message has been received?

Also, if different types of XML messages are being sent by the client, how can the server deterministically know which serialization object to use?

For instance, for an "Inventory" object, this is the code I use:
[PHP]
std::istringstream istr( ostr.str() ); // ostr contains the XML data recv'd from TCP socket
boost::archive::xml_iarchive ia( istr );

Inventory inv;
ia >> BOOST_SERIALIZATION_NVP( inv );

std::cout << "Inventory:\n" << inv << std::endl;
[/PHP]
I perform no sanity checks prior to using the Boost serialization library to populate the Inventory object.  Suppose I want to be able to handle different XML data, other than just the "Inventory" data; how would I check which type of data I have received before making a wild assumption that it's Inventory data?  Suppose it were BankingData, or some other type of data?

---

### Post by dribeas on 2008-07-31
> **dwhitney67 said:**
> I am experimenting with the C++ XML Serialization Boost library for a simple server application.

I would recomend that you emailed the [boost-users list]("mailto:boost-users@lists.boost.org") it is quite active and both users and library writers answer there.

   David

---

