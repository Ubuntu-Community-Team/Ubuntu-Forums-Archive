---
title: "PostgreSQL C++ API"
date: 2010-09-27
forum: Programming Talk
---

### Post by mickeoliver on 2010-09-27
Hello,

does anyone know a good tutorial/guide on libpq or libpqxx?

I'm doing a small project with c++ and a need a PostgreSQL database.

The documentation and references are good, ([http://www.postgresql.org/docs/8.4/static/libpq.html](http://www.postgresql.org/docs/8.4/static/libpq.html) [http://pqxx.org/devprojects/libpqxx/doc/stable/html/Tutorial/](http://pqxx.org/devprojects/libpqxx/doc/stable/html/Tutorial/))
but I still can't figure out how to actually use them in practice.

Thanks!

---

### Post by dumbsnake on 2010-09-27
I'm a C++ programmer, but I personally really prefer libpq over libpqxx myself. I've included some sample code in case it is helpful to you. It illustrates using the main features of Postgres from C++. I'm sorry if it isn't helpful:

```
#include "postgresql/libpq-fe.h"

// because integers in PostGres are sent in "Network byte order" (big endian)
#include <netinet/in.h>


namespace {
  PGconn *connection;
  
  void initialize_database_connection(){
    connection = PQconnectdb("dbname = wk_userdb");
    if(PQstatus(connection) != CONNECTION_OK){
      connection = 0;
      throw (PVBException() << "Unable to connect to the User Database");
    }
  }
  
  void shutdown_database_connection(){
    if(connection){
      PQfinish(connection);
    }
  }

...


  void create_user(const UserID &user_id){
    ::std::uint32_t user_id_for_postgres[2] = {htonl(user_id.address[1]), htonl(user_id.address[2])};

    // create a public/private key
    char n[256];
...
    EncryptNS::generate_rsa_key(256, n, d);
...

    // save the public key to the database
    {
      const char *command = "INSERT INTO user_keys(user_id, public_key) VALUES($1, $2);";
      const char *values[2] = {reinterpret_cast<const char *>(user_id_for_postgres), n};
      int formats[2] = {1, 1}; // this means that we are sending both fields in binary
      int lengths[2] = {8, 256}; // This tells Postgres the lengths of the fields
      
      // execute the 'command' on 'connection', it has 2 arguments
      PGresult* insert_public_key_result = PQexecParams(connection, command, 2, 0, values, lengths, formats, 1);

      if(PQresultStatus(insert_public_key_result) != PGRES_COMMAND_OK){
        ::std::cerr << "FATAL ERROR: There was an exception writing the public key into the database for User(" << user_id << ") using command '" << command << "': " << PQerrorMessage(connection) << ::std::endl;
        PQclear(insert_public_key_result);
        return;
      }
      PQclear(insert_public_key_result);
    }
    
    // create a user resource
    const char *command = "SELECT peer_addresses, user_authorizations, actual_name, user_profile FROM users WHERE user_id = $1;";
    const char *values[1] = {reinterpret_cast<const char *>(user_id_for_postgres)};
    int lengths[1] = {8};
    int formats[1] = {1};
    PGresult* get_user_info_result = PQexecParams(connection, command, 1, 0, values, lengths, formats, 1);

    if(PQresultStatus(get_user_info_result) != PGRES_TUPLES_OK){
      ::std::cerr << "FATAL ERROR: There was an exception fetching the data for User(" << user_id << ") from  the database using command '" << command << "': " << PQerrorMessage(connection) << ::std::endl;
      PQclear(get_user_info_result);
      return;
    }
...
  }
...
}

```

---

### Post by mickeoliver on 2010-09-28
Thanks a lot, I'll have a look at that.

---

