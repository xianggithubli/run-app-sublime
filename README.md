
# Run applications - Sublime Text

Run any customized application from command palette. Just Ctrl/Command+Shift+P, input `Run: XXX`, that's it!

![effect](./imgs/screenshot.png)

## Installation Instructions

**Package Installer**

* Install [Sublime Package Control](http://wbond.net/sublime_packages/package_control)
* Select "Package Control: Install Package" from the Command Palette (`super/ctrl+shift+p`)
* Find "Run Apps" and select

**Git clone**
* Enter directory through "Browse Packages..." in Sublime Text "Preferences"
* Run
    ```
    git clone https://github.com/liuhewei/run-app-sublime.git
    ```

## Usage
Firstly, add applications through: "Tools" -> "Run Apps" -> "Add Application".

Each application follows:
```
    {
        "caption": "Run: Git",  // Run: <App-name>, shown in command pallete
        "command": "runapp",    // cannot be changed
        "args":{
          // application full path on Win/Linux, or only name on MAC
          "app": "",

          // argument list
          // variables can be use: $DIR$, $FILE$, $PROJ$
          "args": [""],

          // optional: define what should follow the command
          // default is None
          // "dir" - file directory, same as $DIR$
          // "file" - file name, same as $FILE$
          // "proj" - project directory, same as $PROJ$
          "type": "",

          // optional: command line application or not
          // default is false
          "cli": true

          // optional: send in selected text as input or not
          // default is false
          "input": true
        }
    }
```

Take "Git bash on windows" as an example for GUI-app, the original command is:

`C:/Windows/system32/wscript "D:/Tools/Git/Git Bash.vbs" <directory>`

```json
    {
        "caption": "Run: Git",
        "command": "runapp",
        "args":{
          "app": "C:\\Windows\\system32\\wscript",
          "args": ["D:\\Tools\\Git\\Git Bash.vbs"],
          "type": "proj"
        }
    }
```

Take "git status ." as an example for CLI-app, the original command is:

`D:\Tools\Git\mingw64\bin\git.exe status .` Under current file's directory.

```json
{
    "caption": "Run: Git-status",
    "command": "runapp",
    "args":{
      "app": "D:\\Tools\\Git\\mingw64\\bin\\git.exe",
      "args": ["status", "."],
      "type": "dir",
      "cli": true
    }
}
```

Take "go doc <package>" as an example for CLI-app with input, the original command is:

`D:\Tools\Go\bin\go.exe doc fmt.Println` Under selected text `fmt.Println`

```json
{
    "caption": "Run: Godoc",
    "command": "runapp",
    "args":{
      "app": "D:\\Tools\\Go\\bin\\go.exe",
      "args": ["doc"],
      "input": true,
      "cli": true
    }
}
```
