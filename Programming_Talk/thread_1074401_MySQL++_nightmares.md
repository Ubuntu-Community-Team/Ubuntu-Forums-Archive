---
title: "MySQL++ nightmares"
date: 2009-02-19
forum: Programming Talk
---

### Post by gvanto on 2009-02-19
I'm pulling my hair out trying to get this MySQL++ libary on my Kubuntu machine to work...

I've followed the (rather limited) instructions on the website ([http://tangentsoft.net/mysql++/]("http://tangentsoft.net/mysql++/"))
for getting it installed.

I downloaded the source (mysql++-3.0.9.tar.gz) - which features some pretty bad readme texts: doesn't say how to build it lol - so after yet another google search, think i eventually did it with 'make' and 'make install'
(in case I need to: is there a way to check if this installed correctly, and if need be, uninstall it?) Below is output of make install ...

now, when i include:
#include <mysql++.h>,

eclipse recognises it. in fact, it recognizes mysqlpp::Connection, as well as mysqlpp::Query,

HOWEVER, it does NOT recognize (and gives 'make' error: Description	Resource	Path	Location	Type
&#8216;Result&#8217; is not a member of &#8216;mysqlpp&#8217;	WLClient.cpp	WLClient/src	36	C/C++ Problem) mysqlpp::StoreQueryResult nor mysqlpp::Result -> how this happens I am not sure but it's causing me great grief !

Help would be much appreciated!

> 
pacific@mainbox:~/tmp2/mysql++-3.0.9$ ls
aclocal.m4       cleanmf        config.sub    examples        INSTALL.txt         Makefile.simple    README-Cygwin.txt    README-Unix.txt        Wishlist
Bakefiles.bkgen  config         configure     exrun           lib                 mysql++.bkl        README-examples.txt  README-Visual-C++.txt
bk-deps          config.guess   configure.ac  exrun.bat       libmysqlclient.def  mysql++.ebuild     README-Linux.txt     rebake.bat
bmark.txt        config.h       COPYING.txt   HACKERS.txt     LICENSE.txt         mysql++.spec       README-Mac-OS-X.txt  test
bootstrap        config.h.in    CREDITS.txt   install.hta     Makefile            mysql++.spec.in    README-MinGW.txt     vc2003
bootstrap.bat    config.log     doc           install.hta.in  Makefile.in         mysql++.xcodeproj  README-Solaris.txt   vc2005
ChangeLog        config.status  dtest         install-sh      Makefile.mingw      osver              README.txt           vc2008
pacific@mainbox:~/tmp2/mysql++-3.0.9$ make
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_beemutex.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/beemutex.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_connection.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/connection.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_cpool.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/cpool.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_datetime.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/datetime.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_dbdriver.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/dbdriver.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_field_names.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/field_names.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_field_types.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/field_types.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_manip.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/manip.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_myset.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/myset.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_mysql++.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/mysql++.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_mystring.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/mystring.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_null.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/null.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_options.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/options.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_qparms.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/qparms.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_query.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/query.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_result.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/result.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_row.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/row.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_sql_buffer.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/sql_buffer.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_stadapter.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/stadapter.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_tcp_connection.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/tcp_connection.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_transaction.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/transaction.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_type_info.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/type_info.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_uds_connection.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/uds_connection.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_vallist.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/vallist.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o mysqlpp_wnp_connection.o -I. -fPIC -DPIC  -I/usr/include/mysql -g -O2 ./lib/wnp_connection.cpp
g++ -shared -fPIC -o libmysqlpp.so.3.0.9 mysqlpp_beemutex.o mysqlpp_connection.o mysqlpp_cpool.o mysqlpp_datetime.o mysqlpp_dbdriver.o mysqlpp_field_names.o mysqlpp_field_types.o mysqlpp_manip.o mysqlpp_myset.o mysqlpp_mysql++.o mysqlpp_mystring.o mysqlpp_null.o mysqlpp_options.o mysqlpp_qparms.o mysqlpp_query.o mysqlpp_result.o mysqlpp_row.o mysqlpp_sql_buffer.o mysqlpp_stadapter.o mysqlpp_tcp_connection.o mysqlpp_transaction.o mysqlpp_type_info.o mysqlpp_uds_connection.o mysqlpp_vallist.o mysqlpp_wnp_connection.o   -Wl,-soname,libmysqlpp.so.3    -lmysqlclient
(cd .; rm -f libmysqlpp.so libmysqlpp.so.3; ln -s libmysqlpp.so.3.0.9 libmysqlpp.so.3; ln -s libmysqlpp.so.3 libmysqlpp.so)
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o test_array_index_array_index.o -Ilib  -I/usr/include/mysql -g -O2 ./test/array_index.cpp
g++ -o test_array_index test_array_index_array_index.o    -L. -lmysqlclient     -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o test_cpool_cpool.o -Ilib      -I/usr/include/mysql -g -O2 ./test/cpool.cpp
g++ -o test_cpool test_cpool_cpool.o    -L. -lmysqlclient     -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o test_datetime_datetime.o -Ilib  -I/usr/include/mysql -g -O2 ./test/datetime.cpp
g++ -o test_datetime test_datetime_datetime.o    -L. -lmysqlclient     -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o test_inttypes_inttypes.o -Ilib  -I/usr/include/mysql -g -O2 ./test/inttypes.cpp
g++ -o test_inttypes test_inttypes_inttypes.o    -L. -lmysqlclient     -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o test_manip_manip.o -Ilib      -I/usr/include/mysql -g -O2 ./test/manip.cpp
g++ -o test_manip test_manip_manip.o    -L. -lmysqlclient     -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o test_null_comparison_null_comparison.o -Ilib  -I/usr/include/mysql -g -O2 ./test/null_comparison.cpp
g++ -o test_null_comparison test_null_comparison_null_comparison.o    -L. -lmysqlclient     -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o test_qssqls_qssqls.o -Ilib  -I/usr/include/mysql -g -O2 ./test/qssqls.cpp
g++ -o test_qssqls test_qssqls_qssqls.o    -L. -lmysqlclient     -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o test_qstream_qstream.o -Ilib  -I/usr/include/mysql -g -O2 ./test/qstream.cpp
g++ -o test_qstream test_qstream_qstream.o    -L. -lmysqlclient     -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o test_string_string.o -Ilib  -I/usr/include/mysql -g -O2 ./test/string.cpp
g++ -o test_string test_string_string.o    -L. -lmysqlclient     -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o test_tcp_tcp.o -Ilib      -I/usr/include/mysql -g -O2 ./test/tcp.cpp
g++ -o test_tcp test_tcp_tcp.o    -L. -lmysqlclient     -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o test_uds_uds.o -Ilib      -I/usr/include/mysql -g -O2 ./test/uds.cpp
g++ -o test_uds test_uds_uds.o    -L. -lmysqlclient     -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o test_wnp_wnp.o -Ilib      -I/usr/include/mysql -g -O2 ./test/wnp.cpp
g++ -o test_wnp test_wnp_wnp.o    -L. -lmysqlclient     -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o excommon_cmdline.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/cmdline.cpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o excommon_printdata.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/printdata.cpp
rm -f libmysqlpp_excommon.a
ar rcu libmysqlpp_excommon.a excommon_cmdline.o excommon_printdata.o
ranlib libmysqlpp_excommon.a
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o cgi_jpeg_cgi_jpeg.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/cgi_jpeg.cpp
g++ -o cgi_jpeg cgi_jpeg_cgi_jpeg.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o cpool_cpool.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/cpool.cpp
g++ -o cpool cpool_cpool.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o dbinfo_dbinfo.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/dbinfo.cpp
g++ -o dbinfo dbinfo_dbinfo.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o deadlock_deadlock.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/deadlock.cpp
g++ -o deadlock deadlock_deadlock.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o fieldinf_fieldinf.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/fieldinf.cpp
g++ -o fieldinf fieldinf_fieldinf.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o for_each_for_each.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/for_each.cpp
g++ -o for_each for_each_for_each.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o load_jpeg_load_jpeg.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/load_jpeg.cpp
g++ -o load_jpeg load_jpeg_load_jpeg.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o multiquery_multiquery.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/multiquery.cpp
g++ -o multiquery multiquery_multiquery.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o resetdb_resetdb.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/resetdb.cpp
g++ -o resetdb resetdb_resetdb.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o simple1_simple1.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/simple1.cpp
g++ -o simple1 simple1_simple1.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o simple2_simple2.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/simple2.cpp
g++ -o simple2 simple2_simple2.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o simple3_simple3.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/simple3.cpp
g++ -o simple3 simple3_simple3.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o ssqls1_ssqls1.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/ssqls1.cpp
g++ -o ssqls1 ssqls1_ssqls1.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o ssqls2_ssqls2.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/ssqls2.cpp
g++ -o ssqls2 ssqls2_ssqls2.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o ssqls3_ssqls3.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/ssqls3.cpp
g++ -o ssqls3 ssqls3_ssqls3.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o ssqls4_ssqls4.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/ssqls4.cpp
g++ -o ssqls4 ssqls4_ssqls4.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o ssqls5_ssqls5.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/ssqls5.cpp
g++ -o ssqls5 ssqls5_ssqls5.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o store_if_store_if.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/store_if.cpp
g++ -o store_if store_if_store_if.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o tquery1_tquery1.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/tquery1.cpp
g++ -o tquery1 tquery1_tquery1.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o tquery2_tquery2.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/tquery2.cpp
g++ -o tquery2 tquery2_tquery2.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o tquery3_tquery3.o -Ilib      -I/usr/include/mysql -g -O2 ./examples/tquery3.cpp
g++ -o tquery3 tquery3_tquery3.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
/home/pacific/tmp2/mysql++-3.0.9/bk-deps g++ -c -o transaction_transaction.o -Ilib  -I/usr/include/mysql -g -O2 ./examples/transaction.cpp
g++ -o transaction transaction_transaction.o    -L. -lmysqlclient     -lmysqlpp_excommon -lmysqlpp
pacific@mainbox:~/tmp2/mysql++-3.0.9$ make install
/usr/bin/install -c -d /usr/lib
/usr/bin/install -c -m 644 libmysqlpp.so /usr/lib
/usr/bin/install: cannot create regular file `/usr/lib/libmysqlpp.so': Permission denied
make: *** [install_mysqlpp] Error 1
pacific@mainbox:~/tmp2/mysql++-3.0.9$ sudo make install
[sudo] password for pacific:
/usr/bin/install -c -d /usr/lib
/usr/bin/install -c -m 644 libmysqlpp.so /usr/lib
/usr/bin/install -c libmysqlpp.so.3.0.9 /usr/lib
(cd /usr/lib ; rm -f libmysqlpp.so libmysqlpp.so.3; ln -s libmysqlpp.so.3.0.9 libmysqlpp.so.3; ln -s libmysqlpp.so.3 libmysqlpp.so)
/usr/bin/install -c -d /usr/include/mysql++
(cd . ; /usr/bin/install -c -m 644  lib/*.h /usr/include/mysql++)



---

### Post by dwhitney67 on 2009-02-19
> **gvanto said:**
> I'm pulling my hair out trying to get this MySQL++ libary on my Kubuntu machine to work...

I've followed the (rather limited) instructions on the website ([http://tangentsoft.net/mysql++/]("http://tangentsoft.net/mysql++/"))
for getting it installed.

I downloaded the source (mysql++-3.0.9.tar.gz) ...

I'm in a hurry, so I do not have much time to post my reply, but take a look at this code to see if it helps:

DatabaseManager.cpp:
```

//
//  DatabaseManager.cpp
//

#include "DatabaseManager.h"
#include "DatabaseLoginInfo.h"
#include "EventLogEntry.h"
#include "ComSubsystemStatus.h"
#include "ComStatusIndex.h"

using namespace std;


DatabaseManager::DatabaseManager()
{
}

DatabaseManager::~DatabaseManager()
{
  databaseConnection.disconnect();
}

void
DatabaseManager::connectedToServer( const DatabaseLoginInfo& loginInfo )
{
  try
  {
#if 0
    const uint32 connectTimeout = 5;  // seconds

    databaseConnection.connect( loginInfo.database.c_str(),
                                loginInfo.hostname.c_str(),
                                loginInfo.username.c_str(),
                                loginInfo.password.c_str(),
                                0, 0, connectTimeout, 0,
                                CLIENT_MULTI_STATEMENTS );
#endif
    databaseConnection.connect( loginInfo.database.c_str(),
                                loginInfo.hostname.c_str(),
                                loginInfo.username.c_str(),
                                loginInfo.password.c_str());

    // This check is redundant (and probably not needed).  If an error were to
    // occur with the connection attempt, the catch-block below would already
    // have been called (and we would not be here!).
    //
    if ( isConnectSuccessful() )
    {
      // nothing to do here
    }
    else
    {
      failedConnection();
    }
  }
  catch ( mysqlpp::ConnectionFailed& ex )
  {
    // TODO
    //databaseManagerPort.connectFailure().send();
  }
}

void
DatabaseManager::reconnectedToServer( const DatabaseLoginInfo& loginInfo )
{
  connectedToServer( loginInfo );
}

void
DatabaseManager::failedConnection()
{
  // TODO
  //databaseManagerPort.connectFailure().send();
}

void
DatabaseManager::disconnected()
{
  databaseConnection.disconnect();
}

void
DatabaseManager::issuedQuery( const string& queryStatement )
{
  if ( isConnected() )
  {
    DatabaseResults results = issueQuery( queryStatement );

    // TODO
    //databaseManagerPort.queryResults( results ).send();
  }
  else
  {
    // Update Subsystem Status
    //
    ComSubsystemStatus::getInstance().incrementStatus( ComStatusIndex::DATABASE_ACCESS_ERRORS );

    // Issue Event Log
    //
    EventLogEntry entry( EventLogEntry::GENERAL,
                         EventLogEntry::LOW,
                         "DatabaseManager lost its connected to the DB server." );

    // TODO
    //dbEventLogPort.logEvent( entry ).send();

    // TODO
    //databaseManagerPort.connectFailure().send();
  }
}

bool
DatabaseManager::isConnectSuccessful()
{
  return databaseConnection.connected();
}

bool
DatabaseManager::isConnected()
{
  return databaseConnection.ping() == 0;
}


// Utility Methods
//
DatabaseResults
DatabaseManager::issueQuery( const string& queryStatement )
{
  queryResults.clear();

  try
  {
    mysqlpp::Query            query  = databaseConnection.query();
    mysqlpp::StoreQueryResult result = query.store( queryStatement.c_str() );

    if ( result )
    {
      // translate/store result
      //
      queryResults.push_back( DatabaseResult( result ) );


      // Get remaining results, if any
      //
      while ( query.more_results() )
      {
        // translate/store next result(s)
        //
        queryResults.push_back( DatabaseResult( query.store_next() ) );
      }
    }
    else
    {
      // Some SQL queries do not return a result; nevertheless it is necessary to
      // insert a default response to inform the caller that their query succeeded.
      //
      queryResults.push_back( DatabaseResult() );
    }
  }
  catch ( mysqlpp::BadConversion& ex )
  {
    DatabaseResult errorResult( DatabaseResult::BAD_CONVERSION, ex.what() );
    queryResults.push_back( errorResult );
  }
  catch ( mysqlpp::BadFieldName& ex )
  {
    DatabaseResult errorResult( DatabaseResult::BAD_FIELD_NAME, ex.what() );
    queryResults.push_back( errorResult );
  }
  catch ( mysqlpp::BadIndex& ex )
  {
    DatabaseResult errorResult( DatabaseResult::BAD_INDEX, ex.what() );
    queryResults.push_back( errorResult );
  }
  catch ( mysqlpp::BadOption& ex )
  {
    DatabaseResult errorResult( DatabaseResult::BAD_OPTION, ex.what() );
    queryResults.push_back( errorResult );
  }
  catch ( mysqlpp::BadParamCount& ex )
  {
    DatabaseResult errorResult( DatabaseResult::BAD_PARAM_COUNT, ex.what() );
    queryResults.push_back( errorResult );
  }
  catch ( mysqlpp::UseQueryError& ex )
  {
    DatabaseResult errorResult( DatabaseResult::USE_QUERY_ERROR, ex.what() );
    queryResults.push_back( errorResult );
  }
  catch ( mysqlpp::BadQuery& ex )
  {
    DatabaseResult errorResult( DatabaseResult::BAD_QUERY, ex.what() );
    queryResults.push_back( errorResult );
  }
  catch ( mysqlpp::ConnectionFailed& ex )
  {
    DatabaseResult errorResult( DatabaseResult::CONNECTION_FAILED, ex.what() );
    queryResults.push_back( errorResult );
  }
  catch ( mysqlpp::DBSelectionFailed& ex )
  {
    DatabaseResult errorResult( DatabaseResult::DB_SELECTION_FAILED, ex.what() );
    queryResults.push_back( errorResult );
  }
  catch ( mysqlpp::MutexFailed& ex )
  {
    DatabaseResult errorResult( DatabaseResult::MUTEX_FAILED, ex.what() );
    queryResults.push_back( errorResult );
  }
  catch ( mysqlpp::ObjectNotInitialized& ex )
  {
    DatabaseResult errorResult( DatabaseResult::OBJECT_NOT_INITIALIZED, ex.what() );
    queryResults.push_back( errorResult );
  }
  catch ( mysqlpp::TypeLookupFailed& ex )
  {
    DatabaseResult errorResult( DatabaseResult::TYPE_LOOKUP_FAILED, ex.what() );
    queryResults.push_back( errorResult );
  }

  return queryResults;
}

```

DatabaseManager.h:
```

//
//  DatabaseManager.h
//

#ifndef DATABASE_MANAGER_H
#define DATABASE_MANAGER_H

#include "DatabaseResults.h"
#include <string>
#include <mysql++.h>


// Forward Declaration(s)
//
class DatabaseLoginInfo;


class DatabaseManager
{
  public:
    DatabaseManager();

    virtual ~DatabaseManager();

    // Transition lines
    //
    void connectedToServer( const DatabaseLoginInfo& loginInfo );
    void reconnectedToServer( const DatabaseLoginInfo& loginInfo );
    void failedConnection();
    void disconnected();
    void issuedQuery( const std::string& queryStatement );
    bool isConnectSuccessful();
    bool isConnected();

    // Utility methods
    //
    DatabaseResults issueQuery( const std::string& queryStatement );

  private:
    // Defined but not implemented
    //
    DatabaseManager( const DatabaseManager& dbMgr );

    // Member Data
    //
    mysqlpp::Connection databaseConnection;
    DatabaseResults     queryResults;
};

#endif

```

Makefile:
```

CXXFLAGS = -Wall -pedantic -Wno-long-long -O2

MYSQL_INC := $(shell mysql_config --include)
MYSQL_LIB := $(shell mysql_config --libs)

INCPATH  = -I./ \
           $(MYSQL_INC) \
           -I/usr/include/mysql++

LIBDEST  = ../lib
LIB      = libdbMgr.a

LIBSRC   = DatabaseManager.cpp

LIBOBJ   = $(LIBSRC:.cpp=.o)

.cpp.o:
        $(CXX) $(CXXFLAGS) $(INCPATH) -c $< -o $@

libs: $(LIB)

$(LIB): $(LIBOBJ)
        ar r $(LIB) $(LIBOBJ)

install: $(LIB)
        install -m 444 $(LIB) $(LIBDEST)

clean:
        $(RM) $(LIBOBJ)
        $(RM) $(LIB)

cleanall: clean
        $(RM) $(LIBDEST)/$(LIB)

```

---

### Post by gvanto on 2009-02-19
Thanks DWhitney,

have you  built this in eclipse?

Also, do you have the "DatabaseResults.h" file perhaps? This is I guess where you use mysqlpp::StoreQueryResult / mysqlpp::Result (whichever one is supposed to be used!)

I'm still left stumped on how certain classes within the namespace can be valid, yet some are not?

Can i ask which version / how u installed mysql++ ??

many many thanks for ur help!
g

---

### Post by dwhitney67 on 2009-02-19
gvanto

I've attached a tar-ball with the "DatabaseManager" library I developed for a company I supported in the past.  Essentially the manager is a wrapper around MySql++.  The company did not want to tie their application to MySql++, thus the purpose for the wrapper.

Now, I am able to build the DatabaseManager library on my Fedora 9 system, which I believe has version 3.0.9 of the MySql++ library.

On my Ubuntu 8.04, I cannot build the library because of an issue with the mysqlpp::FieldNames.

Here's the anomaly:
```

$ make
$ g++ -Wall -pedantic -Wno-long-long -O2 -I./ -I../Common -I../SubsystemInterfaces/CommonInterface -I../SubsystemInterfaces/EventLogInterface -I/usr/include/mysql -I/usr/include/mysql++ -c DatabaseField.cpp -o DatabaseField.o
In file included from DatabaseField.cpp:6:
DatabaseRow.h:33: error: expected unqualified-id before ‘<’ token
DatabaseRow.h:33: error: expected ‘,’ or ‘...’ before ‘<’ token
make: *** [DatabaseField.o] Error 1

```

Here's the code that is causing the compiler grief:
```

...
class DatabaseRow
{
  public:
    DatabaseRow();

    DatabaseRow( const mysqlpp::Row& row,
                 const mysqlpp::RefCountedPointer<mysqlpp::FieldNames>& fieldNames );
...
};

```

Ubuntu 8.04 has version 2.3.2 of the MySql++ library.  So essentially, Ubuntu is a generation or two off from Fedora's release.  As for how I installed the library, I probably used Synaptic (i.e. apt-get).

---

### Post by gvanto on 2009-02-22
Hi Dwhitney,

Thanks alot for your helpfulness.

Just a quick Q: if the company didn't want dependency on mysql++, wouldn't using a wrapper around it still require them to be reliant on it? (i mean the interface will be different, so I guess they wanted a non-changing interface?)

Anywayz, yeah I find it strange that mysql++ library in the kubuntu repositories is so out of date ... mysql access in c++, this must be one of the most commonly used things ... only reason I want to use it really is because I like the way it makes use of containers and gives iterators to iterate through result sets associatively. (alternative is to write my own integer-index -> associative indexing functionality for the standard mysql.h result set ... but I don't really have the time)

OK I've just built the latest 3.0.0) mysql++  and re-attempted things ...

Think I've got it working (it compiles, and mysqlpp:Result is deprecated anyway) ... but the main culprit was that the 3.0.9 libraries got installed at /usr/local/include/mysql++ rather than /usr/include/mysql++ (which is where the much older aptitude-installed one got put and my eclipse was configured for) ... DOHHHHHH!!

Oh well, at least I have something working now! Thanks Dwhitney again! :)

---

### Post by dwhitney67 on 2009-02-22
gvanto

Yesterday I upgraded my Ubuntu distro to the 8.10 version, and now I am able to compile "99.44%" of the DatabaseManager code I presented earlier.  The only problem is with the following catch-exception clause in DatabaseManager.cpp:
```

...
  catch ( mysqlpp::BadIndex& ex )
  {
    DatabaseResult errorResult( DatabaseResult::BAD_INDEX, ex.what() );
    queryResults.push_back( errorResult );
  }
...

```
After commenting out this piece of code, everything else compiled/linked without problems.

Ubuntu 8.10 has available, via Synaptic, version 3.0.0 of MySql++.

When Ubuntu upgrades MySql++ to version 3.0.9, then the BadIndex exception will be available.

P.S.  My former employer did not want to sprinkle the usage of the MySql++ library all over their application; hence the purpose for the wrapper classes, that essentially translate the interface and the results into a custom interface.  Unfortunately I did not go out of my way to implement an iterator for the results.

---

### Post by gvanto on 2009-02-22
Yeah I guess one has to be wary of which version of a package / library the package manager has in Ubuntu.

MySQL++ seems to be a great library though! (and probably worth the hassle :-)

---

