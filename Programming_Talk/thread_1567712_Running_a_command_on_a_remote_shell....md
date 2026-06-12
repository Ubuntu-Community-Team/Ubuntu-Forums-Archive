---
title: "Running a command on a remote shell..."
date: 2010-09-04
forum: Programming Talk
---

### Post by arkashkin on 2010-09-04
Hi,
I am building a remote shell server which should execute command he gets from the client over a socket.

The server must continue listening for a new connections after it finishes executing a command.

```
int main(int argc, char** argv)
{
..................................
..................................
 
    if ((server_sock = tcp_establish(portNum, BACKLOG)) < 0)
        smperror("rsh_server: Failed establish connection. \n");


    while(true)
    {
        //get a client request to connect
        if ((client_sock = tcp_get_connection(server_sock, (struct sockaddr *)&client)) < 0)
            fprintf(stderr,"rsh_server: Client connection failed.\n");
..................................
..................................

        //if we don't have any pipes.
        if(sub_commands.size()==1)
        {
            dup2(client_sock,STDIN_FILENO);
            dup2(client_sock,STDOUT_FILENO);

            exec_command(sub_commands[0]);
        }
..................................
..................................

        close(client_sock);
    }
    return (EXIT_SUCCESS);
}


void exec_command(char* command)
{
    vector<char*> exec_argv;
    char * arg;
    char * n = NULL;

    arg = strtok(command, " ");
    exec_argv.push_back(arg);

    while ((arg = strtok(NULL, " "))!=NULL)
        exec_argv.push_back(arg);
    exec_argv.push_back(n);

    if(execvp(exec_argv[0], &exec_argv[0])==ERROR)
        perror("faild to execute some command.\n");
}

```

Some how the server (which code I have pasted here..) exits after passing its stdout to the socket. How can I make the server continue running in the infinite loop?

---

### Post by spjackson on 2010-09-04
> **arkashkin said:**
> Some how the server (which code I have pasted here..) exits after passing its stdout to the socket. How can I make the server continue running in the infinite loop?
execvp "replaces the current process image with a new process image." (Quoted from the man page.) So your program stops as soon as the other one starts.

One way to handle this is with fork(), then call execvp in the forked child. This is probably the normal way to do it. Alternatively, you could call system(), provided that it is OK for your server to block while the command executes.

---

