---
title: "Include a C++ variable in MySQL Query"
date: 2012-03-17
forum: Programming Talk
---

### Post by Pierrick584 on 2012-03-17
Hello, i am trying to do a SQL query in my software, and i need it to use user input (more precisely, input incomming from network, but thats half revelant)

i have tried with libmysqlclient and mysql++, the first with the *close quote* + variable + *open quote* (got that from a forum post) and the seccond *close quote* << mysqlpp::quote_only << variable ); (got that from the official doccumentation

Both give me errors about the operator used.

Here is my mysqlpp code right now.

sssql.cpp
```
bool sssql::checklogin(mysqlpp::String user, mysqlpp::String pass)
{
    mysqlpp::String userinput = user;
    mysqlpp::String passcompare = pass;
    mysqlpp::Connection conn(false);


    if (conn.connect(DATABASE, SERVER, USER, PASSWORD))
    {
        mysqlpp::Query query = conn.query("SELECT `password` FROM `account` WHERE `user` = " << mysqlpp::quote_only << userinput);
        mysqlpp::StoreQueryResult res = query.store();
        if (res == userinput)
        {
            std::cout << "Login Succesfull.";
        }
        else
        {
            std::cout << "Login Failled.";
        }

    }
}
```

sssql.h
```
#ifndef SSSQL_H
#define SSSQL_H
//#include "my_global.h" // Include this file first to avoid problems
#include "mysql.h" // MySQL Include File
#define SERVER "localhost"
#define USER "root"
#define PASSWORD "pc"
#define DATABASE "pcnviolagame"
#include <stdio.h>
#include <string>
#include <iostream>
#include <mysql++.h>

class sssql
{
    public:
        sssql();
        virtual ~sssql();

        bool connectdb();
        bool checklogin(mysqlpp::String, mysqlpp::String);
    protected:
    private:
};

#endif // SSSQL_H

```

and the build errors.

```
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|78|warning: "/*" within comment [-Wcomment]|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp||In member function ‘bool sssql::checklogin(mysqlpp::String, mysqlpp::String)’:|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|24|error: no match for ‘operator<<’ in ‘"SELECT `password` FROM `account` WHERE `user` = " << (mysqlpp::quote_only_type0)0u’|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|24|note: candidates are:|
/usr/include/mysql++/datetime.h|217|note: std::ostream& mysqlpp::operator<<(std::ostream&, const mysqlpp::DateTime&)|
/usr/include/mysql++/datetime.h|217|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘std::ostream& {aka std::basic_ostream<char>&}’|
/usr/include/mysql++/datetime.h|339|note: std::ostream& mysqlpp::operator<<(std::ostream&, const mysqlpp::Date&)|
/usr/include/mysql++/datetime.h|339|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘std::ostream& {aka std::basic_ostream<char>&}’|
/usr/include/mysql++/datetime.h|456|note: std::ostream& mysqlpp::operator<<(std::ostream&, const mysqlpp::Time&)|
/usr/include/mysql++/datetime.h|456|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘std::ostream& {aka std::basic_ostream<char>&}’|
/usr/include/mysql++/null.h|350|note: template<class Type, class Behavior> std::ostream& mysqlpp::operator<<(std::ostream&, const mysqlpp::Null<Type, Behavior>&)|
/usr/include/mysql++/tiny_int.h|303|note: template<class VT> std::ostream& mysqlpp::operator<<(std::ostream&, mysqlpp::tiny_int<VT>)|
/usr/include/mysql++/mystring.h|657|note: std::ostream& mysqlpp::operator<<(std::ostream&, const mysqlpp::String&)|
/usr/include/mysql++/mystring.h|657|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘std::ostream& {aka std::basic_ostream<char>&}’|
/usr/include/mysql++/mystring.h|696|note: char mysqlpp::operator<<(mysqlpp::String, char)|
/usr/include/mysql++/mystring.h|696|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|696|note: char mysqlpp::operator<<(char, mysqlpp::String)|
/usr/include/mysql++/mystring.h|696|note:   no known conversion for argument 2 from ‘mysqlpp::quote_only_type0’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|697|note: int mysqlpp::operator<<(mysqlpp::String, int)|
/usr/include/mysql++/mystring.h|697|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|697|note: int mysqlpp::operator<<(int, mysqlpp::String)|
/usr/include/mysql++/mystring.h|697|note:   no known conversion for argument 2 from ‘mysqlpp::quote_only_type0’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|698|note: short int mysqlpp::operator<<(mysqlpp::String, short int)|
/usr/include/mysql++/mystring.h|698|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|698|note: short int mysqlpp::operator<<(short int, mysqlpp::String)|
/usr/include/mysql++/mystring.h|698|note:   no known conversion for argument 2 from ‘mysqlpp::quote_only_type0’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|699|note: long int mysqlpp::operator<<(mysqlpp::String, long int)|
/usr/include/mysql++/mystring.h|699|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|699|note: long int mysqlpp::operator<<(long int, mysqlpp::String)|
/usr/include/mysql++/mystring.h|699|note:   no known conversion for argument 2 from ‘mysqlpp::quote_only_type0’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|701|note: unsigned char mysqlpp::operator<<(mysqlpp::String, unsigned char)|
/usr/include/mysql++/mystring.h|701|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|701|note: unsigned char mysqlpp::operator<<(unsigned char, mysqlpp::String)|
/usr/include/mysql++/mystring.h|701|note:   no known conversion for argument 2 from ‘mysqlpp::quote_only_type0’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|702|note: unsigned int mysqlpp::operator<<(mysqlpp::String, unsigned int)|
/usr/include/mysql++/mystring.h|702|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|702|note: unsigned int mysqlpp::operator<<(unsigned int, mysqlpp::String)|
/usr/include/mysql++/mystring.h|702|note:   no known conversion for argument 2 from ‘mysqlpp::quote_only_type0’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|703|note: short unsigned int mysqlpp::operator<<(mysqlpp::String, short unsigned int)|
/usr/include/mysql++/mystring.h|703|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|703|note: short unsigned int mysqlpp::operator<<(short unsigned int, mysqlpp::String)|
/usr/include/mysql++/mystring.h|703|note:   no known conversion for argument 2 from ‘mysqlpp::quote_only_type0’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|704|note: long unsigned int mysqlpp::operator<<(mysqlpp::String, long unsigned int)|
/usr/include/mysql++/mystring.h|704|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|704|note: long unsigned int mysqlpp::operator<<(long unsigned int, mysqlpp::String)|
/usr/include/mysql++/mystring.h|704|note:   no known conversion for argument 2 from ‘mysqlpp::quote_only_type0’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|711|note: mysqlpp::longlong mysqlpp::operator<<(mysqlpp::String, mysqlpp::longlong)|
/usr/include/mysql++/mystring.h|711|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|711|note: mysqlpp::longlong mysqlpp::operator<<(mysqlpp::longlong, mysqlpp::String)|
/usr/include/mysql++/mystring.h|711|note:   no known conversion for argument 2 from ‘mysqlpp::quote_only_type0’ to ‘mysqlpp::String’|
/usr/include/mysql++/mystring.h|712|note: mysqlpp::ulonglong mysqlpp::operator<<(mysqlpp::String, mysqlpp::ulonglong)|
/usr/include/mysql++/mystring.h|712|note:   no known conversion for argument 1 from ‘const char [49]’ to ‘mysqlpp::String’|
||More errors follow but not being shown.|
||Edit the max errors limit in compiler options...|
||=== Build finished: 50 errors, 1 warnings ===|

```

---

### Post by TeoBigusGeekus on 2012-03-17
Create a string with your query and add your variable with strcat.
If your variable is a number (int, float, double, etc.), convert it to text with snprintf.

---

### Post by Pierrick584 on 2012-03-17
Thanks, i dint though for that, though, now i got some type conversion issue, and tells me that it cannot find the operator ==  .... SQL will ends up driving me crazy... here's the new code and errors

```
        std::string query1 = "SELECT `password` FROM `account` WHERE `user` = '";
        std::string query2 = "'";
        std::string querycomplete;
        strcat (querycomplete, query1 );
        strcat (querycomplete, userinput);
        strcat (querycomplete, query2);
        mysqlpp::Query query = conn.query(querycomplete);
        mysqlpp::StoreQueryResult res = query.store();
```
(yes, i know, some variable are useless there, it isint suposed to be optimised :P)

```
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|83|warning: "/*" within comment [-Wcomment]|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp||In member function ‘bool sssql::checklogin(std::string, std::string)’:|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|26|error: cannot convert ‘std::string {aka std::basic_string<char>}’ to ‘char*’ for argument ‘1’ to ‘char* strcat(char*, const char*)’|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|27|error: cannot convert ‘std::string {aka std::basic_string<char>}’ to ‘char*’ for argument ‘1’ to ‘char* strcat(char*, const char*)’|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|28|error: cannot convert ‘std::string {aka std::basic_string<char>}’ to ‘char*’ for argument ‘1’ to ‘char* strcat(char*, const char*)’|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|31|error: no match for ‘operator==’ in ‘res == userinput’|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|31|note: candidates are:|
/usr/include/mysql++/type_info.h|343|note: bool mysqlpp::operator==(const mysqlpp::mysql_type_info&, const std::type_info&)|
/usr/include/mysql++/type_info.h|343|note:   no known conversion for argument 1 from ‘mysqlpp::StoreQueryResult’ to ‘const mysqlpp::mysql_type_info&’|
/usr/include/mysql++/type_info.h|329|note: bool mysqlpp::operator==(const std::type_info&, const mysqlpp::mysql_type_info&)|
/usr/include/mysql++/type_info.h|329|note:   no known conversion for argument 1 from ‘mysqlpp::StoreQueryResult’ to ‘const std::type_info&’|
/usr/include/mysql++/type_info.h|316|note: bool mysqlpp::operator==(const mysqlpp::mysql_type_info&, const mysqlpp::mysql_type_info&)|
/usr/include/mysql++/type_info.h|316|note:   no known conversion for argument 1 from ‘mysqlpp::StoreQueryResult’ to ‘const mysqlpp::mysql_type_info&’|
/usr/include/c++/4.6/bits/stl_multiset.h|679|note: template<class _Key, class _Compare, class _Alloc> bool std::operator==(const std::multiset<_Key, _Compare, _Alloc>&, const std::multiset<_Key, _Compare, _Alloc>&)|
/usr/include/c++/4.6/bits/stl_set.h|696|note: template<class _Key, class _Compare, class _Alloc> bool std::operator==(const std::set<_Key, _Compare, _Alloc>&, const std::set<_Key, _Compare, _Alloc>&)|
/usr/include/c++/4.6/bits/stl_vector.h|1273|note: template<class _Tp, class _Alloc> bool std::operator==(const std::vector<_Tp, _Alloc>&, const std::vector<_Tp, _Alloc>&)|
/usr/include/c++/4.6/bits/stl_multimap.h|795|note: template<class _Key, class _Tp, class _Compare, class _Alloc> bool std::operator==(const std::multimap<_Key, _Tp, _Compare, _Alloc>&, const std::multimap<_Key, _Tp, _Compare, _Alloc>&)|
/usr/include/c++/4.6/bits/stl_map.h|877|note: template<class _Key, class _Tp, class _Compare, class _Alloc> bool std::operator==(const std::map<_Key, _Tp, _Compare, _Alloc>&, const std::map<_Key, _Tp, _Compare, _Alloc>&)|
/usr/include/c++/4.6/bits/stl_tree.h|846|note: template<class _Key, class _Val, class _KeyOfValue, class _Compare, class _Alloc> bool std::operator==(const std::_Rb_tree<_Key, _Val, _KeyOfValue, _Compare, _Alloc>&, const std::_Rb_tree<_Key, _Val, _KeyOfValue, _Compare, _Alloc>&)|
/usr/include/c++/4.6/bits/stl_tree.h|309|note: template<class _Val> bool std::operator==(const std::_Rb_tree_iterator<_Tp>&, const std::_Rb_tree_const_iterator<_Val>&)|
/usr/include/c++/4.6/bits/stl_list.h|1564|note: template<class _Tp, class _Alloc> bool std::operator==(const std::list<_Tp, _Alloc>&, const std::list<_Tp, _Alloc>&)|
/usr/include/c++/4.6/bits/stl_list.h|275|note: template<class _Val> bool std::operator==(const std::_List_iterator<_Tp>&, const std::_List_const_iterator<_Val>&)|
/usr/include/c++/4.6/bits/stl_deque.h|1917|note: template<class _Tp, class _Alloc> bool std::operator==(const std::deque<_Tp, _Alloc>&, const std::deque<_Tp, _Alloc>&)|
/usr/include/c++/4.6/bits/stl_deque.h|253|note: template<class _Tp, class _RefL, class _PtrL, class _RefR, class _PtrR> bool std::operator==(const std::_Deque_iterator<_Tp, _RefL, _PtrL>&, const std::_Deque_iterator<_Tp, _RefR, _PtrR>&)|
/usr/include/c++/4.6/bits/stl_deque.h|246|note: template<class _Tp, class _Ref, class _Ptr> bool std::operator==(const std::_Deque_iterator<_Tp, _Ref, _Ptr>&, const std::_Deque_iterator<_Tp, _Ref, _Ptr>&)|
/usr/include/c++/4.6/bits/streambuf_iterator.h|194|note: template<class _CharT, class _Traits> bool std::operator==(const std::istreambuf_iterator<_CharT, _Traits>&, const std::istreambuf_iterator<_CharT, _Traits>&)|
/usr/include/c++/4.6/bits/basic_string.h|2460|note: template<class _CharT, class _Traits, class _Alloc> bool std::operator==(const std::basic_string<_CharT, _Traits, _Alloc>&, const _CharT*)|
/usr/include/c++/4.6/bits/basic_string.h|2448|note: template<class _CharT, class _Traits, class _Alloc> bool std::operator==(const _CharT*, const std::basic_string<_CharT, _Traits, _Alloc>&)|
/usr/include/c++/4.6/bits/basic_string.h|2434|note: template<class _CharT> typename __gnu_cxx::__enable_if<std::__is_char<_Tp>::__value, bool>::__type std::operator==(const std::basic_string<_CharT>&, const std::basic_string<_CharT>&)|
/usr/include/c++/4.6/bits/basic_string.h|2427|note: template<class _CharT, class _Traits, class _Alloc> bool std::operator==(const std::basic_string<_CharT, _Traits, _Alloc>&, const std::basic_string<_CharT, _Traits, _Alloc>&)|
/usr/include/c++/4.6/bits/allocator.h|127|note: template<class _Tp> bool std::operator==(const std::allocator<_Tp1>&, const std::allocator<_Tp1>&)|
/usr/include/c++/4.6/bits/allocator.h|122|note: template<class _T1, class _T2> bool std::operator==(const std::allocator<_T1>&, const std::allocator<_T2>&)|
/usr/include/c++/4.6/bits/postypes.h|218|note: template<class _StateT> bool std::operator==(const std::fpos<_StateT>&, const std::fpos<_StateT>&)|
/usr/include/c++/4.6/bits/stl_iterator.h|335|note: template<class _IteratorL, class _IteratorR> bool std::operator==(const std::reverse_iterator<_IteratorL>&, const std::reverse_iterator<_IteratorR>&)|
/usr/include/c++/4.6/bits/stl_iterator.h|285|note: template<class _Iterator> bool std::operator==(const std::reverse_iterator<_Iterator>&, const std::reverse_iterator<_Iterator>&)|
/usr/include/c++/4.6/bits/stl_pair.h|201|note: template<class _T1, class _T2> bool std::operator==(const std::pair<_T1, _T2>&, const std::pair<_T1, _T2>&)|
/usr/include/c++/4.6/ext/new_allocator.h|123|note: template<class _Tp> bool __gnu_cxx::operator==(const __gnu_cxx::new_allocator<_Tp>&, const __gnu_cxx::new_allocator<_Tp>&)|
/usr/include/c++/4.6/bits/stl_iterator.h|805|note: template<class _Iterator, class _Container> bool __gnu_cxx::operator==(const __gnu_cxx::__normal_iterator<_Iterator, _Container>&, const __gnu_cxx::__normal_iterator<_Iterator, _Container>&)|
/usr/include/c++/4.6/bits/stl_iterator.h|799|note: template<class _IteratorL, class _IteratorR, class _Container> bool __gnu_cxx::operator==(const __gnu_cxx::__normal_iterator<_IteratorL, _Container>&, const __gnu_cxx::__normal_iterator<_IteratorR, _Container>&)|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|41|warning: no return statement in function returning non-void [-Wreturn-type]|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp||In member function ‘bool sssql::connectdb()’:|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|45|warning: no return statement in function returning non-void [-Wreturn-type]|
||=== Build finished: 37 errors, 3 warnings ===|

```

---

### Post by TeoBigusGeekus on 2012-03-17
Ok, I hate c++, so I'll post an example in c:
```
int client_id=123;
char sql_query[50], buf[10];
strcpy (sql_query,"SELECT * FROM clients WHERE client_id=");
snprintf(buf,sizeof(buf),"%d",client_id);
strcat(sql_query,buf);
```

---

### Post by Pierrick584 on 2012-03-17
I guess i could try in a char array..

---

### Post by Pierrick584 on 2012-03-17
New version, pretty close to some result, but still errors comparing the result...


```
bool sssql::checklogin(char user[15], char pass[15])
{
    char userinput[15];
    strcpy(userinput, user);
    char passcompare[15];
    strcpy(passcompare, pass);
    mysqlpp::Connection conn(false);


    if (conn.connect(DATABASE, SERVER, USER, PASSWORD))
    {

        char querycomplete[50];
        strcpy (querycomplete, "SELECT `password` FROM `account` WHERE `user` = '");
        strcat (querycomplete, userinput);
        strcat (querycomplete, "'");
        mysqlpp::Query query = conn.query(querycomplete);
        mysqlpp::StoreQueryResult res = query.store();
        if (strcmp(res, passcompare))
        {
            std::cout << "Login Succesfull.";
        }
        else
        {
            std::cout << "Login Failled.";
        }

    }
}
```


error: cannot convert ‘mysqlpp::StoreQueryResult’ to ‘const char*’ for argument ‘1’ to ‘int strcmp(const char*, const char*)’


i hate these types issue <.<

---

### Post by CynicRus on 2012-03-17
```

string sql;
    
    cout << "Please enter  client id: " << endl;
    cin >> sql;
    
    sql = "ELECT * FROM clients WHERE client_id=" + sql;
    query_state = mysql_query(&mysql, sql.c_str());

```

---

### Post by CynicRus on 2012-03-17
You need to use the c_str( ) method of the string type to get a c-style string for the strcmp function.

---

### Post by Pierrick584 on 2012-03-18
Well, now the program technicaly build with the variable beign part of the sql query, yet i cannot compare the result, or even just std::cout it to the terminal to actualy see if the query work'd  (the real goal is actualy to compare it)

Here what i got right now, the tested std::cout is currently commented as it shouldnt be part of the finished version, yet its how it is used to try to show the result, with the if after beign commented.

```
    std::string sqlquery = "SELECT `password` FROM `account` WHERE `user` = '" + userinput + "'";

       MYSQL_RES *result;
    mysql_query(connect, sqlquery.c_str());
    result = mysql_store_result(connect);
    // std::cout << result;

        if (strcmp(result, passcompare.c_str()))
        {
            std::cout << "Login Succesfull.";
        }
        else
        {
            std::cout << "Login Failled.";
        }

return 0;
```

Once again, aint sure if every sql code is right, most come from manual / tutorials, yet i did end up showing up some random database value with similar code in previous test (the sql query was just irrevelant to my project, and ended up modifying all that to get what i currently got)

---

### Post by dwhitney67 on 2012-03-18
> **Pierrick584 said:**
> 
Once again, aint sure if every sql code is right, ...

Why did you go from using MySQL++ library to using the C-style MySQL library?

Something like this should work:
```

void issueQuery(const std::string& queryStatement)
{
    try
    {
        mysqlpp::Query            query  = dbConn.query();
        mysqlpp::StoreQueryResult result = query.store(queryStatement.c_str());

        ...
    }
    catch (Exception& e)
    {
    }
}

```
The result for the query should be stored in the variable "result".  If you have multiple results, then you should iterate through the query object to obtain each result; for example:
```

    while (query.more_results())
    {
        result = query.store_next();

        ...
    }

```
As for the mysqlpp::StoreQueryResult object, you play with it like this:
```

    // If you want the field names for the rows in the result
    //
    const mysqlpp::RefCountedPointer<mysqlpp::FieldNames>& fieldNames = result.field_names();

    // To analyze each row in the result
    //
    mysqlpp::StoreQueryResult::const_iterator it;

    for (it = result.begin(); it != result.end(); ++it)
    {
        mysqlpp::Row row = *it;

        for (size_t field = 0; field < row.size(); ++field)
        {
            // Get the data within the field
            //
            const string rowData = row[field].c_str();

            ...
        }
    }

```

I have not worked with MySQL++ in many years, so if you still have additional questions, you may want to consider perusing the documentation here: [http://tangentsoft.net/mysql++/doc/html/refman/index.html](http://tangentsoft.net/mysql++/doc/html/refman/index.html)

The User Manual link is on that page, however in case you want to get straight to it, here's that link:  [http://tangentsoft.net/mysql++/doc/html/userman/index.html](http://tangentsoft.net/mysql++/doc/html/userman/index.html)

---

### Post by Pierrick584 on 2012-03-18
Even though it doesnt realy answer my problem, it did clarify a few things, so thanks. but the current problem reside in the fact that i cannot do anything with result, no matter what i try to do, the compiler complain about types thing, the only thing i can do with it, is a std::cout, but even then, it does not actualy show up in the program (maybe it is my sql query that is wrong... (the C++ usage, not the actual query as i tested it in phpmyadmin)

I did check the doccumentation and it doesnt seems to explain much my specific problem, their example always use the result for different things, i did not saw an example of comparing a single sql value with a C++ variable, its always about getting a large array and processing it in a loop... anyway, if someone does have an idea to compare the result, or spot anything in my query, let me know.

Oh and by the way, i did switch from mysqlpp beacause, well i have two version of the code, i try them back and forth as mysqlpp tend to give me pretty weird errors, it just doesnt get the job done as it says it should, i tried using mysqlpp::String everywhere, and i still have type issue... oh and beacause i got suggested to use the string.c_str()  i figured this function might not be available in the mysqlpp string


by the way this code does gives the folowing errors, 
```
bool sssql::checklogin(std::string user, std::string pass)
{
    std::string userinput = user;
    std::string passcompare = pass;

    mysqlpp::Connection conn(false);
    if (conn.connect(DATABASE, SERVER, USER, PASSWORD))
    {
        std::string sqlquery = "SELECT `password` FROM `account` WHERE `user` = '" + userinput + "'";
        mysqlpp::Query            query  = conn.query();
        mysqlpp::StoreQueryResult result = query.store(sqlquery.c_str());
      

  if (strcmp(result, passcompare.c_str()))
        {
            std::cout << "Login Succesfull.";
        }
        else
        {
            std::cout << "Login Failled.";
        }

return 0;
}


```


```
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|141|warning: "/*" within comment [-Wcomment]|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp||In member function ‘bool sssql::checklogin(std::string, std::string)’:|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|89|error: cannot convert ‘mysqlpp::StoreQueryResult’ to ‘const char*’ for argument ‘1’ to ‘int strcmp(const char*, const char*)’|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|101|error: a function-definition is not allowed here before ‘{’ token|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|103|error: expected ‘}’ at end of input|
/home/pierrick/programming/netsandbox/sssql/sssql.cpp|103|warning: control reaches end of non-void function [-Wreturn-type]|
||=== Build finished: 3 errors, 2 warnings ===|

```

---

### Post by dwhitney67 on 2012-03-18
```
bool sssql::checklogin(std::string user, std::string pass)
{
    std::string userinput = user;
    std::string passcompare = pass;

```
What is the point of creating yet another copy of the user and password strings??  First of call, the function parameters should be declared as const std::string references, not what you have; otherwise you are making a copy of the strings that are passed in (very inefficient).  And then you make copies of these copies!
```

bool sssql::checklogin(**const std::string& user, const std::string& pass**)
{
    //NOT NEEDED std::string userinput = user;
    //NOT NEEDED std::string passcompare = pass;

    mysqlpp::Connection conn(false);
    if (conn.connect(DATABASE, SERVER, USER, PASSWORD))
    {
        std::string sqlquery = "SELECT `password` FROM `account` WHERE `user` = '" + **user** + "'";
        mysqlpp::Query            query  = conn.query();
        mysqlpp::StoreQueryResult result = query.store(sqlquery.c_str());

        ...

```

And why are you treating the mysqlpp::StoreQueryResult object as if it were a C-Style null-terminated string with this silly statement?
```

  if (strcmp(result, pass.c_str()))

```
If you had read what I posted earlier with a little more care, you would have found the appropriate way to process a StoreQueryResult.  You need to obtain the row(s) from the result, and from there get the information you seek.

I have no idea what type of data you will get with your query result, and whether it will cotains one or more rows.  Figure this out by iterating over each Row.  Again a recap:
```

    mysqlpp::StoreQueryResult::const_iterator it;

    for (it = result.begin(); it != result.end(); ++it)
    {
        mysqlpp::Row row = *it;

        for (size_t field = 0; field < row.size(); ++field)
        {
            // Get the data within the field
            //
            **const string rowData = row[field].c_str();**   // row[field] is a mysqlpp::String object

            std::cout << "rowData[" << field << "] = " << rowData << std::endl;
        }
    }

```
The 'rowData' contains the information that you want to compare with your password.  Perhaps you only have one row to example; perhaps more?

----------

EDIT:  Perhaps you can get away with this:
```

    ...

    const mysqlpp::Row row = *result.begin();

    if (pass == row.at(0).c_str())
    {
    }

```

---

### Post by Pierrick584 on 2012-03-18
Well sorry if i missed some obivious part in your previous post, sincerely, i do care about the answer i get. I have some C++ experience, but nothing great, and definitely nothing related to third party library, so i get confused easily, there is many aspect of programming i did not met in my previous (and limited) experience, i barely know a good ammount of theory, but general books never talk about using third party library and how to deal with them.

The silly reimplementation of the user and password's variable is caused by the fact that i changed my code often, i tried various things, and i did that at one point to fix some kind of compiler issue that i cannot remember, and it realy might be irrevelant right now, but i happened to keep it even though i might have removed the "need" at some point, anyway, i am not yet optimising the code, but i do apreciate that you point this out, sincerely.

About the row's.. the type of data i expect is a single word text from the mysql database, i just want to extract the "password" that is in the same line that the "user" that i pass though variable, so there is no point to check many row's, i expect one word only from the sql, i did though i could completely skip the row loop beacause of that, am i right? or is it needed to do this and compare the password's input to the row loop result in some way? i never though of giving it a shot, and i'm wondering if it wouldnt include a few multiline character (even though the lines would be empty) that would make the compareason fail.


By the way if you think of a better way to check if the user and password that the user typed in is matching the database, i'm listening, thats just the way that i though it could work with my small experience (inexistant, database wise)

I'm gonna try your code suggestion now, and give more news, i sincerely apreciate the help, sorry for having so much issue understanding and implementing your suggestions :(...

---

### Post by Pierrick584 on 2012-03-18
Well! this compareason code you just gave me compiled perfectly! now though the server seems not to actualy reach the compareason... so i added alot of std::cout to see what the server actualy reach (i've been too lazy to debug, even though i'm kinda comfortable with it :P) And it block at the sql query string composition, maybe my variable input result some errors... i guess i'm kinda back to the first problem, hehe, Thanks alot for the help with the compareason though, thats awesome! 


Now i gotta find a way to give my query in some acceptable way.


Here's the current code btw..

```
 
    mysqlpp::Connection conn(false);
    if (conn.connect(DATABASE, SERVER, USER, PASSWORD))
    {
       std::cout << "Connection to the database Succesfull. We now create the query string with " << userinput << " to compare the result with " << passcompare <<".\n";
        std::string sqlquery = "SELECT `password` FROM `account` WHERE `user` = '" + userinput + "'";
        std::cout << "We now execute the query...";
        mysqlpp::Query            query  = conn.query();
        std::cout << "Query Executed.";
        mysqlpp::StoreQueryResult result = query.store(sqlquery.c_str());
        std::cout << "The result has been stored, lets process the row.";
    const mysqlpp::Row row = *result.begin();
    std::cout << "Row processing done. lets compare it";
    if (passcompare == row.at(0).c_str())
     //   if (strcmp(result, passcompare.c_str()))
        {
            std::cout << "Login Succesfull.";
        }
        else
        {
            std::cout << "Login Failled.";
        }


    }
```last output i get is this..        std::cout << "Connection to the database Succesfull. We now  create the query string with " << userinput << " to compare  the result with " << passcompare <<".\n";

---

### Post by Pierrick584 on 2012-03-18
Okay... i decided to work on with the debugger a bit... something quite weird happened... i placed a breakpoint at the begining of my std::cout (the first one that i see) then i proceeded line per line, and every line seems to process even though i dont see the others std::cout in the console... then i keep going, line per line, trying to observe whats going on, at some point it exit this function and go back in the main program, go though a tons of different lines, if and other stuff, (including the line where the server says the client connection get lost... since, the connection actualy drop cause the server run in debugger..)

and after the message that say that we lost the client, there is a break (once again, before the break, no message has been shown to the console) and after the break, EVERY previous std::cout get shown at the same time (including the one that says that the login was succesfull... YAY the query actualy work... it seems)


I realy dont understand why console messages get blocked... thats realy weird..

---

### Post by Some Penguin on 2012-03-18
Incidentally, please do NOT structure you code like that unless you have very rigorously validated and performed any necessary escaping on the user input.

What if the user input were
```

';DROP TABLE account CASCADE;

```

for instance?

---

### Post by Pierrick584 on 2012-03-18
No worries, i'm quite aware of the common (and a few less common) hacking techniques, and i am building as much code as possible as shared libraries (this one including) so i can correct those stupid misstake i make while strugling to fix a bug without forgetting an instance of it somewhere else, and of course i will put anti sql injection code client and server side, i'm just realy not there yet.

Thanks for worrying though :)

---

