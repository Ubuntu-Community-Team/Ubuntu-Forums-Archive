---
title: "MySQL C API problem"
date: 2006-08-09
forum: Programming Talk
---

### Post by anroy on 2006-08-09
Not sure if I will find an answer here but it is worth a try. :)

I set up MySQL 5.0.24 on an Ubuntu Linux machine, by downloading the source tarball.

For some reason I just can't seem to get mysql_init to work, it ALWAYS returns NULL!

On the MySQL site it says that this happens if there is insufficient memory.  I am sure that is not the case here.

Here is my code.
```
#include </usr/local/mysql/include/mysql/mysql.h>
#include <stdio.h>
#include <string.h>

int main()
{
	MYSQL mysql;
	rc = mysql_init( &mysql );
	if( rc == NULL ) {
		printf( "mysql_init returns NULL" );
	}
}
```


I also tried the following variation, with the same NULL results.
```
#include </usr/local/mysql/include/mysql/mysql.h>
#include <stdio.h>
#include <string.h>

int main()
{
	MYSQL *mysql;
	mysql = mysql_init( NULL );
	if( mysql == NULL ) {
		printf( "mysql_init returns NULL" );
	}

}
```

Does anybody have even the slightest clue as to why I would get NULL?

I compiled and linked using the following:
gcc sql_prog.c -o sql_prog -lz -lmysqlclient -L /usr/local/mysql/lib/mysql/

The compile and link were successful, as the message "mysql_init returns NULL" is properly output!

Also, the database server runs fine, the client programs mysqlshow, mysqladmin, etc. work fine.  They were also compiled on the same machine (I installed from source).

I am thinking about copying one of the client folders (like mysqlshow) in the MySQL source, modifying the code so it does what I need, and including it in the overall MySQL build as another Client.

However it is very time-consuming to configure and make the entire MySQL each time.  Maybe I can use this option?
shell> ./configure --without-server

Does this have any effect on the server that I am not aware of, like removing any files or settings?  I just want to rebuild the clients but want to leave the server as is.

Thanks,
Arka N. Roy

---

### Post by anroy on 2006-08-10
Sorry it turns out this was a false alarm.  Please forgive me for having wasted your time.

The lesson here is to check more carefully before posting to a forum.

---

### Post by zakariae_tr on 2010-12-01
[COLOR=#000000]Hello everyone, I  want to write a C program that uses the API to communicate with a MySQL  database but I can not locate where there is an error!


[/COLOR]```


[COLOR=Green]#include <stdio.h>
#include <stdlib.h>
#include <mysql/mysql.h>


int main(int argc, char*argv[])
{
    MYSQL *conn;

    MYSQL_RES *result;
    MYSQL_ROW elementsColonne;

    unsigned int nbColonnes;
    int i;
    // initialisation
    if((conn = mysql_init(NULL)) == NULL)
    {
        printf("Erreur d'initialisation\n");
        return 0;
    }

    // connexion au serveur (ici, en local)
    if(mysql_real_connect(conn,"localhost","root","zakariae","ma_base",0,NULL,0)!=0)
    {
        printf("Erreur de connexion\n");
        return 0;
    }
    printf("Connexion reussit\n");
    // on lance la requête
    if (mysql_query(conn,"INSERT INTO `ma_base`.`table` (`nom`, `prenom`, `login`, `passe`) VALUES('zakaria', 'tahir', 'jellol','12')")==0)
        printf("Insertion faite\n");
    else
        printf("Erreur dans l'insertion \n");

    if (mysql_query(conn,"SELECT * FROM table")==0)
    {
        printf("Erreur dans la requête\n");
        return;
    }
    else // requête bonne, traitons les données qu'elle renvoit
    {
        result = mysql_store_result(conn);
        if (result != NULL)  // MySQL peut extraire des résultats
        {
            nbColonnes = mysql_num_fields(result);

            // récupère les enregistrements un par un
            while ((elementsColonne = mysql_fetch_row(result)))
            {
                for (i = 0; i < nbColonnes; i++)
                    printf("%s\t", (elementsColonne[i] != NULL) ? elementsColonne[i] : "NULL");
                printf("\n");
            }
            // on libère la mémoire prise pour les résultats
            mysql_free_result(result);
        }
        else
            printf("Aucun résultat à la requête !\n");
    }

    // on ferme la connexion au serveur MySQL
    mysql_close(conn);
}[/COLOR]

```

---

