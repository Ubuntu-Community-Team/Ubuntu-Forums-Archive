---
title: "PHP: Sock it's!"
date: 2010-08-29
forum: Programming Talk
---

### Post by Sailor5 on 2010-08-29
Ahoy Sailors!

It's been noted this isn't the best language to use, But for reasons I can't explain, I want to use PHP. I found a script on the net that allows connections of multiple scripts (via sockets) to be handled, Which is perfect for what I need, However when I adapt it to sending data between ALL the connected scripts, it becomes picky & doesn't send to everyone(Which is the problem).

I emailed the author & he said
""The active sockets are probably located in an array, sending a message  to every client would be a matter of iterating over each client and  sending the data.""

However I'm unable to script the cure(never did anything above echoing & editing HTML in PHP) I'm sure the smart people here at ubuntu forums.org will know what to do.

Here's the master.php[php]<?php 
 
/* 
 
Simple "echo back" TCP server. 
 
*/ 
 
include("supersocket.class.php"); 
 
##### FIRST WITH OUR CALLBACKS ##### 
function newdata($socket_id, $channel_id, $buffer, &$obj) 
    {        
                echo "What do you want to send?\n"; 
                $buffer = fread(STDIN, 80);
                $obj->write($socket_id, $channel_id, $buffer); 
    } 
 
$socket = new SuperSocket(array("*:404")); // will listen on ALL IPs over port 10000 
$socket->assign_callback("DATA_SOCKET_CHANNEL", "newdata"); 
$socket->start(); 
$socket->loop(); 
?>[/php]And here's the SUPER SOCKET class![php] 
Class SuperSocket 
    { 
        var $listen = array(); 
        var $status_listening = FALSE; 
        var $sockets = array(); 
        var $event_callbacks = array(); 
        var $recvq = 2; 
        var $parent; 
         
        function SuperSocket($listen = array('127.0.0.1:6667')) 
            { 
                $listen = array_unique($listen); 
                foreach ($listen as $address) 
                    { 
                        list($address, $port) = explode(":", $address, 2); 
                        $this->listen[] = array("ADDR" => trim($address), "PORT" => trim($port)); 
                    }; 
            } 
         
        function start() 
            { 
                if ($this->status_listening) 
                    { 
                        return FALSE; 
                    }; 
                $this->sockets = array(); 
                $cursocket = 0; 
                foreach ($this->listen as $listen) 
                    { 
                        if ($listen['ADDR'] == "*") 
                            { 
                                $this->sockets[$cursocket]['socket'] = socket_create_listen($listen['PORT']); 
                                $listen['ADDR'] = FALSE; 
                            } 
                        else 
                            { 
                                $this->sockets[$cursocket]['socket'] = socket_create(AF_INET, SOCK_STREAM, SOL_TCP); 
                            }; 
                        if ($this->sockets[$cursocket]['socket'] < 0) 
                            { 
                                return FALSE; 
                            }; 
                        if (@socket_bind($this->sockets[$cursocket]['socket'], $listen['ADDR'], $listen['PORT']) < 0) 
                            { 
                                return FALSE; 
                            }; 
                        if (socket_listen($this->sockets[$cursocket]['socket']) < 0) 
                            { 
                                return FALSE; 
                            }; 
                        if (!socket_set_option($this->sockets[$cursocket]['socket'], SOL_SOCKET, SO_REUSEADDR, 1)) 
                            { 
                                return FALSE; 
                            }; 
                        if (!socket_set_nonblock($this->sockets[$cursocket]['socket'])) 
                            { 
                                return FALSE; 
                            }; 
                        $this->sockets[$cursocket]['info'] = array("ADDR" => $listen['ADDR'], "PORT" => $listen['PORT']); 
                        $this->sockets[$cursocket]['channels'] = array(); 
                        $this->sockets[$cursocket]['id'] = $cursocket; 
                        $cursocket++; 
                    }; 
                $this->status_listening = TRUE; 
            } 
         
        function new_socket_loop(&$socket) 
            { 
                $socket =& $this->sockets[$socket['id']]; 
                if ($newchannel = @socket_accept($socket['socket'])) 
                    { 
                        socket_set_nonblock($newchannel); 
                        $socket['channels'][]['socket'] = $newchannel; 
                        $channel = array_pop(array_keys($socket['channels'])); 
                        $this->remote_address($newchannel, $remote_addr, $remote_port); 
                        $socket['channels'][$channel]['info'] = array('ADDR' => $remote_addr, 'PORT' => $remote_port); 
                        $event = $this->event("NEW_SOCKET_CHANNEL"); 
                        if ($event) 
                        $event($socket['id'], $channel, $this); 
                    }; 
            } 
         
        function recv_socket_loop(&$socket) 
            { 
                $socket =& $this->sockets[$socket['id']]; 
                foreach ($socket['channels'] as $channel_id => $channel) 
                    { 
                        $status = @socket_recv($channel['socket'], $buffer, $this->recvq, 0); 
                        if ($status === 0 && $buffer === NULL) 
                            { 
                                $this->close($socket['id'], $channel_id); 
                            } 
                        elseif (!($status === FALSE && $buffer === NULL)) 
                            { 
                                $event = $this->event("DATA_SOCKET_CHANNEL"); 
                                if ($event) 
                                $event($socket['id'], $channel_id, $buffer, $this); 
                            }; 
                    } 
            } 
         
        function stop() 
            { 
                $this->closeall(); 
                $this->status_listening = FALSE; 
                foreach ($this->sockets as $socket_id => $socket) 
                    { 
                        socket_shutdown($socket['socket']); 
                        socket_close($socket['socket']); 
                    }; 
                $event = $this->event("SERVER_STOP"); 
                if ($event) 
                $event($this); 
            } 
         
        function closeall($socket_id = NULL) 
            { 
                if ($socket_id === NULL) 
                    { 
                        foreach ($this->sockets as $socket_id => $socket) 
                            { 
                                foreach ($socket['channels'] as $channel_id => $channel) 
                                    { 
                                        $this->close($socket_id, $channel_id); 
                                    } 
                            } 
                    } 
                else 
                    { 
                        foreach ($this->sockets[$socket_id]['channels'] as $channel_id => $channel) 
                            { 
                                $this->close($socket_id, $channel_id); 
                            }; 
                    }; 
            } 
         
        function close($socket_id, $channel_id) 
            { 
                $arrOpt = array('l_onoff' => 1, 'l_linger' => 1); 
                @socket_shutdown($this->sockets[$socket_id]['channels'][$channel_id]['socket']); 
                @socket_close($this->sockets[$socket_id]['channels'][$channel_id]['socket']); 
                $event = $this->event("LOST_SOCKET_CHANNEL"); 
                if ($event) 
                $event($socket_id, $channel_id, $this); 
            } 
         
        function loop() 
            { 
                while ($this->status_listening) 
                    { 
                        foreach ($this->sockets as $socket) 
                            { 
                                $this->new_socket_loop($socket); 
                                $this->recv_socket_loop($socket); 
                            }; 
                        $event = $this->event("END_SOCKET_CHANNEL"); 
                        if ($event) 
                        $event($this); 
                    }; 
            } 
         
        function write($socket_id, $channel_id, $buffer) 
            {     
                @socket_write($this->sockets[$socket_id]['channels'][$channel_id]['socket'], $buffer); 
            } 
         
        function get_channel_info($socket_id, $channel_id) 
            { 
                return $this->sockets[$socket_id]['channels'][$channel_id]['info']; 
            } 
         
        function get_socket_info($socket_id) 
            { 
                $socket_info = $this->sockets[$socket_id]['info']; 
                if (empty($socket_info['ADDR'])) 
                    { 
                        $socket_info['ADDR'] = "*"; 
                    }; 
                return $socket_info; 
            } 
         
        function get_raw_channel_socket($socket_id, $channel_id) 
            { 
                return $this->sockets[$socket_id]['channels'][$channel_id]['socket']; 
            } 
         
        function remote_address($channel_socket, &$ipaddress, &$port) 
            { 
                socket_getpeername($channel_socket, $ipaddress, $port); 
            } 
         
        function event($name) 
            { 
                if (isset($this->event_callbacks[$name])) 
                return $this->event_callbacks[$name]; 
            } 
         
        function assign_callback($name, $function_name) 
            { 
                $this->event_callbacks[$name] = $function_name; 
            } 
    }; 
 
?>[/php]Anyone able to fix this?

Thanks Bye!

---

