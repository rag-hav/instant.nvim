instant.nvim
============

**instant.nvim** is a **collaborative** editing plugin for **Neovim** written in **Lua** with no dependencies.

**This is in prototype stage. It should work but some important features are still missing!**
**The transfer protocol is not optimized for large files transfer!**

* [Design document](docs/design.md)
* [Protocol](docs/protocol.md)
* [Commands](docs/commands.md)


Features
--------

* Live editing with multiple users

* Share a whole directory

* See who is editing

Requirements
------------

* Neovim 0.5 (but might work on previous versions)

Install
-------

Install using a plugin manager usuch as [vim-plug](https://github.com/junegunn/vim-plug)

```
Plug 'jbuyki/instant.nvim'
```

Configurations
--------------

* Set your username in your $MYVIMRC. This **must be** set to start or join a server.

```
lua vim.g.instant_username = "YOUR USERNAME"
```

Usage
-----

1. Fire up the server using [node.js](https://nodejs.org/en/) (server/ws_server.js).
2. Create a sharing folder and name it **client1**.
```
mkdir client1
```
3. Start neovim into this folder.
```
cd client1/
neovim
```
4. Make sure the current folder is correct with `:pwd`. It will put all the files on the server! But don't worry if the folder is not empty, it will display an error.

5. Connect the first client with `InstantStart`.
```
:InstantStart 127.0.0.1 8080
```

6. Create another folder and name it **client2**. Start the second instance of neovim.
```
mkdir client2
cd client2/
neovim
```

7. Join the connection with `InstantJoin`.
```
:InstantJoin 127.0.0.1 8080
```

8. Now all files should be sync up!

Todo
----

* Multiple sessions on the same server
* Try to reconnect after connection failure
* TLS support
* tests
