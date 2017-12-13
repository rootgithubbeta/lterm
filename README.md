		          __       ________   _______   _____   _     _    __
                    |  |     |__    __| |   ____| |  _  | | \   / |   \ \           
                    |  |        |  |    |  |__    | |_| | |  \_/  |    \ \          
                    |  |      o |  |    |     |   |   __| |   _   |     \ \         
                    |  |      o |  |    |   __|   |   \   |  | |  |     / /         
                    |  |____  o |  |    |  |____  |    \  |  | |  |    / / ____   
                    |_______| o |__|    |_______| |__|\_\ |__| |__|   /_/ |____|  

# lterm: Online bash terminal(emulator) tutorial

Check out the site live at  -->  [![lterm](https://img.shields.io/badge/webiste-live-brightgreen.svg?style=flat-square)](https://sr6033.github.io/lterm/)	[![Gitter](https://badges.gitter.im/gitterHQ/gitter.svg)](https://gitter.im/lterm/Lobby?utm_source=share-link&utm_medium=link&utm_campaign=share-link)

**lterm** is an online **Terminal Eminulator**. It is a step by step tutorial that will teach you the **bash** commands by making you execute them. 

*Nothing is better than learning by doing.*

It is fully online and doesn't require any extra shitty access. Being an emulator, it only virtualizes a terminal environment and so the commands executed doesn't effect either the server or your local machine. 

### List of commands available presently

- `echo`-----[To display a string]
- `pwd`------[Shows you the present working directory]
- `ls`-------[Lists all the files]
- `cd`-------[To change directory - change the current working directory to a specific directory]
- `cd ..`-----[Moves you up one directory(parent)]
- `cat`------[Concatenate and print the content of files]
- `clear`----[Clears the terminal screen]
- `touch`----[Changes file timestamps or creates a new file]
- `cp`/`mv`--[To copy/move files]
- `rm`-------[Delets a file/directory]
- `uname`----[Shows the name of the Linux/Unix system you are using]
- `data`-----[Shows the local standard date & time]
- `ifconfig`-[Shows information about active network interfaces.]
- `mkdir`----[Creates a new directory]
- `tty`------[Prints the file name of the terminal connected to standard input]

### List of commands that can be added

- `export`
- `history`
- `less`
- `more`

### Contributing 

- Developers who want to contribute, [![fork](https://img.shields.io/badge/style-0-green.svg?style=social&label=Fork&link=https://github.com/sr6033/lterm/fork&link=https://github.com/sr6033/lterm/network)](https://github.com/sr6033/lterm/fork) this repo and edit the file **<a href="https://github.com/sr6033/lterm/blob/master/js/main.js">main.js</a>** to add your commands. 
- You don't have to worry about any other files or programs.

---

- If a **command** doesn't need further steps:

```
// without argument
ls: function() {
        this.echo('This is the ls command\n');
}
```

```
// with argument
echo: function(arg1) {
        this.echo('This is the echo command' + arg1 + '\n');
}
```

- If a **command** needs further steps:

```
cd: function(arg1) {
	this.push(function(cmd, term) {
                if(cmd == 'another_command')
                    this.echo('another_command');
		}, {
                    prompt: '[[b;#44D544;]lterm@localhost/' + arg1 + ':~$] ',
                   }
        );
}
```

---

**IMPORTANT**

- On addition of a new **command**, increase the size of `arr` array. This array acts like a counter to check if a **task/command** is completed or not.
- Example: If I add the command - `echo`. I will add another 0 to the end of `arr`. Then I will make `arr[index] = 1` under `echo` command.
```
var arr = [0,0,0,0,0,0,0,0,0,0,0,0,0,0]; // Will add another 0 here. The place where you added is the index.
...
...
echo: function(arg1) {
            arr[index_where_you_added_0] = 1;	// Will make the value at that index to 1. 	
            this.echo(arg1 + '\n');
            this.echo('> The [[b;#ff3300;]echo] command prints back your arguments.');
            this.echo('> Type [[b;#ff3300;]help] and check your first task is completed.');
            this.echo('> Now type [[b;#ff3300;]pwd] to continue.');
},

```
- If you face any problem or cannot understand anything, open up an **issue**.
- You can also edit the **readme** and make it more user friendly to help out new contributers.

> **NOTE: Kindly keep the diplay of the terminal intact while making an update. A single extra space can make the look of the emulator little odd. So keep that in mind while printing something using `echo` command.**

> Note: Kindly have interpretable & good commit messages. Don't assume me to be some **Jedi** with powers to be able to make out every commit with a single word as message.
*May the Force be with you.*
