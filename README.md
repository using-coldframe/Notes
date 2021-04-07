# Using Coldframe

Creating Ada Applications from UML Models using the ColdFrame Code Generator

## Linux Setup

Here's how to set up ColdFrame on a fresh installation of [Linux Mint 20.1](https://linuxmint.com/edition.php?id=284) with GNAT Community Edition 2020 as your Ada Compiler.

### Preparing the Platform

Start a terminal in your home directory and enter the following commands to install Tcl/Tk and Python Lex-Yacc.
```
sudo apt install tk
sudo apt install tk-dev
sudo apt install python-ply
sudo ln -s /usr/bin/python2 /usr/bin/python
```
Add the following to the end of your .profile file.
```
# Ada
PATH="/opt/GNAT/2020/bin:$PATH"
MANPATH=/opt/GNAT/2020/share/man:$MANPATH

# ColdFrame
export COLDFRAME=$HOME/coldframe
export ADA_PROJECT_PATH=$COLDFRAME:$COLDFRAME/extras:$ADA_PROJECT_PATH

# Saxon (for ColdFrame)
export SAXON_CLASSPATH=$HOME/saxon/saxon.jar

# Scripted Testing (for ColdFrame)
export ADA_PROJECT_PATH=$HOME/scripted_testing:$ADA_PROJECT_PATH

# Tcl Ada SHell (for ColdFrame)
export ADA_PROJECT_PATH=$HOME/tcladashell:$ADA_PROJECT_PATH

# Xpath In Ada (for ColdFrame)
export ADA_PROJECT_PATH=$HOME/xia:$ADA_PROJECT_PATH
```

Perform a system restart.

### Installing GNAT

Download the [GNAT Community Edition 2020 Installer](https://community.download.adacore.com/v1/4d99b7b2f212c8efdab2ba8ede474bb9fa15888d?filename=gnat-2020-20200429-x86_64-linux-bin), start a terminal in your Downloads directory and enter the following commands.
```
chmod +x gnat-2020-20200429-x86_64-linux-bin
sudo ./gnat-2020-20200429-x86_64-linux-bin
```
Accept the default options until installation is complete.

### Installing the Ada Libraries

#### Tcl Ada SHell
Download the [latest Tcl Ada SHell archive](https://github.com/simonjwright/tcladashell/archive/refs/heads/master.zip) and extract the contents to ~/tcladashell.

Start a terminal in that directory and enter the following command. In the window that pops up, click the save button.
```
./setup.tcl
```

Then, enter the following command.
```
make all
```

#### Scripted Testing
Download the [latest Scripted Testing archive](https://github.com/simonjwright/scripted_testing/archive/refs/heads/master.zip) and extract the contents to ~/scripted_testing.

Start a terminal in that directory and enter the following command.
```
gprbuild -p -P scripted_testing
```

#### Xpath In Ada
Download the [latest Xpath in Ada archive](https://github.com/simonjwright/xia/archive/refs/heads/master.zip) and extract the contents to ~/xia. Start a terminal in that directory and enter the following commands.
```
cd test
gprbuild -p -P test.gpr test_xpath
```
### Installing Saxon
Download the [Saxon 6.5.5 archive](https://sourceforge.net/projects/saxon/files/saxon6/6.5.5/saxon6-5-5.zip/download) and extract the contents to ~/saxon.

### Installing ColdFrame
Download the [latest ColdFrame archive](https://github.com/simonjwright/coldframe/archive/refs/heads/master.zip) and extract the contents to ~/coldframe. Start a terminal in that directory and enter the following command.
```
make setup
```
As a confidence check, enter the following commands.
```
cd examples
make
```

### Installing ArgoUML

Download the [ArgoUML 0.35 archive](https://github.com/argouml-tigris-org/argouml/releases/download/VERSION_0_35_1/ArgoUML-0.35.1.tar.gz) and extract the contents to ~/argouml. Start a terminal in that directory and enter the following command.
```
./argouml.sh
```
Set up as described [here](https://simonjwright.github.io/coldframe/argouml-installation.html).
