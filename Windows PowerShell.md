# 🛡️ Windows PowerShell — Complete Notes

A free, comprehensive guide to learning Windows PowerShell — from basics to system administration and cybersecurity use cases.

> **Provided by [Zero2NullSecurity](https://github.com/)** — Free Learning Resources

---

## Table of Contents

- [Introduction to PowerShell](#introduction-to-powershell)
- [What Is PowerShell?](#what-is-powershell)
- [PowerShell Basics](#powershell-basics)
- [Navigating the File System](#navigating-the-file-system-and-working-with-files)
- [Piping, Filtering, and Sorting](#piping-filtering-and-sorting-data)
- [System and Network Information](#system-and-network-information)
- [Real-Time System Analysis](#real-time-system-analysis-in-powershell)

---

## Introduction to PowerShell

### Overview

PowerShell is a powerful command-line shell and scripting environment developed by Microsoft for managing and automating Windows systems. It allows users and administrators to interact with the operating system through commands and scripts.

PowerShell is widely used in **system administration, automation, troubleshooting, and cybersecurity**.

### Learning Objectives

1. What PowerShell is and its capabilities
2. The basic structure of PowerShell commands
3. How to execute basic PowerShell commands
4. How PowerShell is used in the cybersecurity industry

### Applications in Cybersecurity

- **System Enumeration:** Collecting information about Windows systems
- **Process Investigation:** Identifying running and suspicious processes
- **Network Investigation:** Gathering network configuration information
- **Log Analysis:** Accessing and investigating Windows event logs
- **Automation:** Automating repetitive security tasks
- **Active Directory Enumeration:** Gathering information about domain environments during authorized security assessments

### Key Takeaway

PowerShell is an important tool for Windows system administration and cybersecurity. Learning its commands and scripting capabilities helps security professionals investigate, manage, and automate Windows environments.

---

## What Is PowerShell?

### 1. Introduction to PowerShell

PowerShell is a command-line shell and scripting language developed by Microsoft. It is used for **task automation, system administration, and configuration management**.

PowerShell consists of three main components:

#### 1.1 Command-Line Shell

A command-line shell allows users to interact with an operating system by executing commands.

```powershell
Get-Process
```

This command displays the currently running processes.

#### 1.2 Scripting Language

PowerShell provides its own scripting language. Users can write multiple commands in a script file and execute them automatically. It helps automate repetitive tasks such as checking processes, managing services, and collecting system information.

#### 1.3 Configuration Management Framework

PowerShell helps administrators manage and configure systems.

Examples:
- Managing Windows services
- Managing user accounts
- Changing system configurations
- Automating administrative tasks

### 2. PowerShell and CMD

| CMD | PowerShell |
|-----|------------|
| Traditional command-line tool | Advanced command-line shell |
| Primarily text-based output | Object-based output |
| Supports batch scripting | Supports advanced scripting |
| Limited automation capabilities | Powerful automation capabilities |

> PowerShell works with **structured objects**, while traditional CMD commands primarily work with **text**.

### 3. PowerShell and .NET

PowerShell uses the **.NET platform** to interact with system components and perform administrative operations. .NET provides libraries and tools that help developers build applications and software. PowerShell uses these capabilities to perform advanced system management and automation.

### 4. Cross-Platform Support

Initially, PowerShell was designed for Windows. Later, Microsoft introduced **PowerShell Core**, which expanded PowerShell support to multiple operating systems.

PowerShell is now available on:
- Windows
- Linux
- macOS

> **Note:** Windows PowerShell 5.1 is Windows-specific, while modern PowerShell 7+ supports Windows, Linux, and macOS.

### 5. A Brief History of PowerShell

PowerShell was developed to overcome the limitations of traditional Windows command-line tools.

- **Early 2000s:** Windows administrators faced difficulties automating complex administrative tasks using CMD and batch files.
- **Jeffrey Snover:** A Microsoft engineer who introduced an object-oriented approach to Windows command-line management.
- **2006 — PowerShell Release:** Microsoft released Windows PowerShell in 2006.
- **2016 — Open-Source Announcement:** Microsoft announced plans to make PowerShell open source and cross-platform. PowerShell Core 6.0 was subsequently released in 2018.

### 6. Understanding Objects in PowerShell

An **object** is a programming structure that contains data and functionality. An object has two important components:

#### 6.1 Properties

Properties describe the characteristics or information of an object.

Example: A car object may contain:
- Color
- Model
- FuelLevel

#### 6.2 Methods

Methods represent the actions an object can perform.

Example: A car object may have:
- `Drive()`
- `HonkHorn()`
- `Refuel()`

#### Objects in PowerShell

```powershell
Get-Process
```

This command returns process objects containing information such as:
- `ProcessName`
- `Id`
- `CPU`
- `WorkingSet`

### 7. Text-Based Output vs Object-Based Output

**CMD:**
```cmd
tasklist
```
Displays running processes as text.

**PowerShell:**
```powershell
Get-Process
```
Returns structured process objects.

We can select specific properties using:

```powershell
Get-Process | Select-Object ProcessName, Id
```

This displays only the process names and process IDs.

### 8. What is a Cmdlet?

A **cmdlet** (pronounced *command-let*) is a PowerShell command designed to perform a specific operation. PowerShell cmdlets generally follow the **Verb-Noun** naming convention.

| Cmdlet | Purpose |
|--------|---------|
| `Get-Process` | Retrieves running processes |
| `Get-Service` | Retrieves system services |
| `Get-Location` | Displays the current location |
| `Get-ChildItem` | Lists files and directories |
| `Stop-Process` | Stops a running process |
| `Start-Service` | Starts a service |

### 9. PowerShell in Cybersecurity

- **SOC Analysis:** Collecting system information and investigating running processes
- **Incident Response:** Investigating suspicious activities
- **Penetration Testing:** Performing authorized security testing
- **System Administration:** Managing Windows systems and automating tasks

### 10. Key Takeaways

- PowerShell is developed by Microsoft
- It is a command-line shell and scripting language
- It supports task automation and configuration management
- It uses objects instead of relying only on text
- Objects contain properties and methods
- Cmdlets generally follow the Verb-Noun naming convention
- Modern PowerShell supports Windows, Linux, and macOS

---

## PowerShell Basics

### 1. Lab Environment Setup

To practice the commands in this guide, you can use:

- **A Windows machine** (physical or virtual) with PowerShell installed
- **A Windows VM** running in a hypervisor such as VirtualBox, VMware, or Hyper-V
- **A remote SSH session** to a Windows machine, if remote access is configured

#### Connecting to a Remote Windows Machine

If you are practising on a remote Windows system:

1. Ensure SSH or remote management is enabled on the target machine
2. Connect using an SSH client (for example, OpenSSH or PuTTY)
3. Use valid credentials configured on that system

> ⚠️ **Security Note:** Never commit real passwords, API keys, or credentials to a public repository. Always sanitize your notes before publishing.

### 2. Launching PowerShell

PowerShell can be launched in several ways:

1. **Start Menu** – Search for PowerShell
2. **Run Dialog** – Press `Win + R`, type `powershell`, and press Enter
3. **File Explorer** – Type `powershell` in the address bar
4. **Task Manager** – Use `File > Run new task`
5. **Command Prompt** – Type `powershell` and press Enter

After launching, the prompt changes to something like:
```
PS C:\Users\YourName>
```

The `PS` prefix indicates that we are working inside the PowerShell shell.

### 3. Basic Syntax — Verb-Noun

PowerShell commands are generally called **cmdlets**. Cmdlets usually follow the **Verb-Noun** naming convention.

- **Verb:** Describes the action
- **Noun:** Specifies the object or resource on which the action is performed

Examples:

```powershell
Get-Content
Get-Content file.txt
```
Retrieves and displays the contents of a file.

```powershell
Set-Location
Set-Location C:\Users
```
Changes the current working directory.

### 4. Basic Cmdlets

#### 4.1 Get-Command

Lists the commands available in the current PowerShell session.

```powershell
Get-Command
```

Command types:
- Alias
- Function
- Cmdlet
- Script

Filter by type:

```powershell
Get-Command -CommandType "Function"
Get-Command -CommandType Cmdlet
```

#### 4.2 Get-Help

Provides documentation about PowerShell commands.

```powershell
Get-Help Get-Date
```

Displays information such as:
- **NAME:** Command name
- **SYNOPSIS:** Short description
- **SYNTAX:** Command structure
- **DESCRIPTION:** Detailed explanation
- **RELATED LINKS:** Related commands and resources

Useful options:

```powershell
Get-Help Get-Date -Examples
Get-Help Get-Date -Detailed
Get-Help Get-Date -Full
Get-Help Get-Date -Online
```

#### 4.3 Get-Alias

An **alias** is a shortcut or alternative name for a PowerShell cmdlet.

```powershell
Get-Alias
```

Common aliases:

| Alias | Actual Cmdlet |
|-------|---------------|
| `cd` | `Set-Location` |
| `dir` | `Get-ChildItem` |
| `cat` | `Get-Content` |
| `clear` | `Clear-Host` |
| `%` | `ForEach-Object` |
| `?` | `Where-Object` |

Find the actual command behind an alias:

```powershell
Get-Alias cd
```

> **Remember:**
> - **Cmdlet** is the actual PowerShell command
> - **Alias** is a shortcut for a command

### 5. Finding and Downloading Cmdlets

#### What is a Module?

A PowerShell **module** is a package containing related cmdlets, functions, and other resources. Modules provide additional functionality to PowerShell.

#### PowerShell Gallery

An online repository where users can discover and download PowerShell modules.

🌐 **Website:** https://www.powershellgallery.com/

#### 5.1 Find-Module

Searches for modules in online repositories.

```powershell
Find-Module -Name "PowerShell*"
```

- `Find-Module`: Searches for available modules
- `-Name`: Specifies the module name
- `PowerShell*`: Searches for module names beginning with PowerShell

> The `*` character is called a **wildcard**. It can represent different characters in a search pattern.

#### 5.2 Install-Module

Installs a module from an online repository.

```powershell
Install-Module -Name "PowerShellGet"
```

> **Note:** These commands require internet access. In isolated or offline lab environments, module installation will not work.

### 6. Important Terminology

| Term | Meaning |
|------|---------|
| SSH | Secure Shell protocol for remote access |
| Cmdlet | A PowerShell command |
| Verb-Noun | Standard cmdlet naming convention |
| Parameter | Additional input that controls command behaviour |
| Alias | Shortcut or alternative name for a command |
| Function | A reusable block of PowerShell code |
| Module | Package containing related PowerShell commands and resources |
| Wildcard | Character used to match different text patterns |
| Repository | Location where packages and modules are stored |

### 7. Key Takeaways

- PowerShell can be launched directly from CMD
- Cmdlets generally follow the Verb-Noun naming convention
- `Get-Command` lists available commands
- `Get-Help` provides command documentation
- `Get-Alias` displays command shortcuts
- Modules extend PowerShell functionality
- `Find-Module` searches online repositories
- `Install-Module` installs additional modules
- Module installation requires internet access

---

## Navigating the File System and Working with Files

### 1. Introduction

PowerShell provides several cmdlets for navigating directories and managing files:

- List files and directories
- Change the current directory
- Create files and directories
- Delete files and directories
- Copy and move files
- Read file contents

### 2. Get-ChildItem

Displays files and directories in a specified location.

```powershell
Get-ChildItem
```

List items from a specific location:

```powershell
Get-ChildItem -Path "C:\Users\YourName\Documents"
```

**Common equivalents:**

| Environment | Command |
|-------------|---------|
| CMD | `dir` |
| PowerShell | `Get-ChildItem` |
| Linux | `ls` |

### 3. Set-Location

Changes the current working directory.

```powershell
Set-Location -Path ".\Documents"
```

Other examples:

```powershell
Set-Location ..
Set-Location C:\Users\YourName\Downloads
```

**Important path symbols:**
- `.` represents the current directory
- `..` represents the parent directory

> CMD equivalent: `cd`

### 4. New-Item

Creates new files and directories.

#### 4.1 Create a Directory

```powershell
New-Item -Path ".\myfolder\subfolder" -ItemType "Directory"
```

#### 4.2 Create a File

```powershell
New-Item -Path ".\myfolder\subfolder\notes.txt" -ItemType "File"
```

**Important parameters:**
- `-Path`: Specifies the location and name
- `-ItemType`: Specifies whether to create a file or directory

### 5. Remove-Item

Deletes files and directories.

#### 5.1 Delete a File

```powershell
Remove-Item -Path ".\myfolder\subfolder\notes.txt"
```

#### 5.2 Delete a Directory

```powershell
Remove-Item -Path ".\myfolder\subfolder"
```

Remove a directory and its contents recursively:

```powershell
Remove-Item -Path ".\myfolder" -Recurse
```

> ⚠️ **Important:** Always verify the target path before deleting files or directories.

**CMD equivalents:**
- `del` – Deletes files
- `rmdir` – Removes directories

### 6. Copy-Item

Copies files and directories from one location to another.

```powershell
Copy-Item -Path ".\myfolder\file.txt" -Destination ".\myfolder\file-copy.txt"
```

**Important parameters:**
- `-Path`: Specifies the source item
- `-Destination`: Specifies the destination location

> CMD equivalent: `copy`

### 7. Move-Item

Moves files and directories from one location to another.

```powershell
Move-Item -Path ".\file.txt" -Destination ".\myfolder\file.txt"
```

**Important parameters:**
- `-Path`: Specifies the source item
- `-Destination`: Specifies the destination location

> CMD equivalent: `move`

### Copy-Item vs Move-Item

| Copy-Item | Move-Item |
|-----------|-----------|
| Creates a duplicate | Transfers the original item |
| Original remains in its location | Original is removed from its previous location |
| Useful for backups | Useful for organizing files |

### 8. Get-Content

Reads and displays the contents of a file.

```powershell
Get-Content -Path ".\file.txt"
```

**Common equivalents:**

| Environment | Command |
|-------------|---------|
| CMD | `type` |
| PowerShell | `Get-Content` |
| Linux | `cat` |

### 9. Practical Command Summary

| Command | Description |
|---------|-------------|
| `Get-ChildItem` | Lists files and directories |
| `Set-Location` | Changes the current directory |
| `New-Item` | Creates files and directories |
| `Remove-Item` | Deletes files and directories |
| `Copy-Item` | Copies files and directories |
| `Move-Item` | Moves files and directories |
| `Get-Content` | Reads file contents |

### 10. PowerShell in Cybersecurity

- **Get-ChildItem:** Explore directories and locate files
- **Set-Location:** Navigate between investigation directories
- **Get-Content:** Read logs and configuration files
- **Copy-Item:** Create copies of files for investigation
- **Move-Item:** Organize investigation files

### 11. Key Takeaways

- PowerShell uses cmdlets to manage the file system
- `Get-ChildItem` lists files and directories
- `Set-Location` changes the current working directory
- `New-Item` creates files and directories
- `Remove-Item` deletes files and directories
- `Copy-Item` creates copies of files and directories
- `Move-Item` transfers files and directories
- `Get-Content` reads file contents

---

## Piping, Filtering, and Sorting Data

### 1. Introduction to Piping

**Piping** allows the output of one command to become the input of another command. In PowerShell, the pipe operator is `|`.

PowerShell piping passes **objects** instead of only plain text. These objects contain properties and methods that can be used by other cmdlets.

```powershell
Get-ChildItem | Sort-Object Length
```

- `Get-ChildItem`: Retrieves files and directories
- `|`: Passes the output to the next cmdlet
- `Sort-Object Length`: Sorts objects based on their Length property

### 2. Sort-Object

Sorts objects based on specified properties.

```powershell
Get-ChildItem | Sort-Object Length
```

Sort in descending order (largest files first):

```powershell
Get-ChildItem | Sort-Object Length -Descending
```

### 3. Where-Object

Filters objects based on specified conditions.

```powershell
Get-ChildItem | Where-Object -Property "Extension" -eq ".txt"
```

Displays only items with the `.txt` extension.

#### Important Comparison Operators

| Operator | Meaning |
|----------|---------|
| `-eq` | Equal to |
| `-ne` | Not equal to |
| `-gt` | Greater than |
| `-ge` | Greater than or equal to |
| `-lt` | Less than |
| `-le` | Less than or equal to |
| `-like` | Matches a specified pattern |

#### Examples

```powershell
# Equal to
Get-ChildItem | Where-Object -Property Extension -eq ".txt"

# Not equal to
Get-ChildItem | Where-Object -Property Extension -ne ".txt"

# Greater than
Get-ChildItem | Where-Object -Property Length -gt 1000

# Greater than or equal to
Get-ChildItem | Where-Object -Property Length -ge 1000

# Less than
Get-ChildItem | Where-Object -Property Length -lt 1000

# Less than or equal to
Get-ChildItem | Where-Object -Property Length -le 1000

# Pattern matching (wildcard *)
Get-ChildItem | Where-Object -Property Name -like "note*"
```

> The `*` wildcard represents zero or more characters.

### 4. Select-Object

Selects specific properties from objects or limits the number of objects returned.

```powershell
Get-ChildItem | Select-Object Name, Length
```

Display only the first five processes:

```powershell
Get-Process | Select-Object -First 5
```

### 5. Combining Multiple Cmdlets

#### Practical Example: Find the Largest File

```powershell
Get-ChildItem -File |
Sort-Object Length -Descending |
Select-Object -First 1
```

**Explanation:**
1. `Get-ChildItem -File`: Retrieves files and excludes directories
2. `Sort-Object Length -Descending`: Sorts files from largest to smallest
3. `Select-Object -First 1`: Selects the first result

To display only the file name and size:

```powershell
Get-ChildItem -File |
Sort-Object Length -Descending |
Select-Object -First 1 Name, Length
```

### 6. Select-String

Searches for specific text or patterns inside files. Similar to `grep` in Unix and `findstr` in Windows CMD.

```powershell
Select-String -Path ".\notes.txt" -Pattern "password"
```

Output includes:
- File name
- Matching line number
- Matching text

**Important parameters:**
- `-Path`: Specifies the file location
- `-Pattern`: Specifies the text or pattern to search for

### 7. Regular Expressions (Regex)

**Regex** (Regular Expression) is a pattern-matching technique used to search for complex text patterns.

```powershell
Select-String -Path ".\application.log" -Pattern "\d{3}"
```

Searches for three consecutive digits in the file.

- `\d`: Matches a digit from 0 to 9
- `{3}`: Matches exactly three occurrences

> Regex is useful for searching patterns in logs, configuration files, and other text documents.

### 8. Important Cmdlets Summary

| Cmdlet | Purpose |
|--------|---------|
| `Sort-Object` | Sorts objects |
| `Where-Object` | Filters objects |
| `Select-Object` | Selects specific properties or objects |
| `Select-String` | Searches for text patterns |
| `Get-ChildItem` | Retrieves files and directories |

### 9. PowerShell in Cybersecurity

- **Piping:** Combines multiple commands for efficient analysis
- **Sort-Object:** Sorts processes, files, and other collected information
- **Where-Object:** Filters information based on specific conditions
- **Select-Object:** Displays only relevant information
- **Select-String:** Searches logs and files for suspicious text patterns
- **Regex:** Matches complex patterns in text and logs

### 10. Key Takeaways

- Piping connects multiple cmdlets using the `|` operator
- PowerShell pipelines pass objects between cmdlets
- `Sort-Object` arranges objects based on properties
- `Where-Object` filters objects using conditions
- `Select-Object` selects specific properties or limits results
- `Select-String` searches for text patterns inside files
- Regex helps perform advanced pattern matching

---

## System and Network Information

### 1. Introduction

PowerShell provides several cmdlets to retrieve detailed information about a computer system and its network configuration.

In this section, we will learn four important cmdlets:

1. `Get-ComputerInfo`
2. `Get-LocalUser`
3. `Get-NetIPConfiguration`
4. `Get-NetIPAddress`

### 2. Get-ComputerInfo

Retrieves detailed information about a Windows system, including:

- Operating system
- Windows version and build
- Hardware specifications
- BIOS details
- Windows edition
- Installation information

```powershell
Get-ComputerInfo
```

**Important properties:**

| Property | Description |
|----------|-------------|
| WindowsBuildLabEx | Windows build information |
| WindowsCurrentVersion | Windows version information |
| WindowsEditionId | Windows edition |
| WindowsInstallationType | Installation type |
| WindowsInstallDateFromRegistry | Windows installation date |
| WindowsProductId | Windows product identification |
| WindowsProductName | Windows product name |

**Example output:**
```
WindowsEditionId        : Professional
WindowsInstallationType : Client
WindowsProductName      : Windows 11 Pro
```

> CMD equivalent: `systeminfo`

### 3. Get-LocalUser

Displays all local user accounts available on a Windows system.

```powershell
Get-LocalUser
```

**Important properties:**

| Property | Description |
|----------|-------------|
| Name | Local username |
| Enabled | Indicates whether the account is enabled |
| Description | Information about the account |

**Example output:**
```
Name               Enabled Description
----               ------- -----------
Administrator      True    Built-in administrator account
User               True    Local user account
Guest              False   Built-in guest account
```

**Understanding `Enabled`:**
- `True`: The account is enabled
- `False`: The account is disabled

> **Cybersecurity Use:** SOC analysts can use this cmdlet to investigate local accounts and identify unexpected or suspicious user accounts.

> **Important:** `Get-LocalUser` retrieves local accounts, not the complete list of Active Directory domain users.

### 4. Get-NetIPConfiguration

Retrieves network configuration information from the system's network interfaces.

```powershell
Get-NetIPConfiguration
```

**Important properties:**

| Property | Description |
|----------|-------------|
| InterfaceAlias | Network interface name |
| InterfaceIndex | Network interface identification number |
| InterfaceDescription | Network adapter description |
| NetProfile.Name | Connected network profile name |
| IPv4Address | Assigned IPv4 address |
| IPv4DefaultGateway | Default gateway address |
| DNSServer | Configured DNS server |

**Example output:**
```
InterfaceAlias     : Ethernet
IPv4Address        : 192.168.1.15
IPv4DefaultGateway : 192.168.1.1
DNSServer          : 192.168.1.1
```

> CMD equivalent: `ipconfig`

> **Cybersecurity Use:** Helps investigate network connectivity and understand the network configuration of a Windows machine.

### 5. Get-NetIPAddress

Displays detailed information about IP addresses configured on the system's network interfaces (both IPv4 and IPv6).

```powershell
Get-NetIPAddress
```

**Important properties:**

| Property | Description |
|----------|-------------|
| IPAddress | Configured IP address |
| InterfaceIndex | Network interface index |
| InterfaceAlias | Network interface name |
| AddressFamily | IPv4 or IPv6 |
| Type | IP address type |
| PrefixLength | Network prefix length |
| PrefixOrigin | Source of the network prefix |
| SuffixOrigin | Source of the host portion |
| AddressState | Current IP address state |

#### IPv4 and IPv6 Examples

- **IPv4:** `192.168.1.15`
- **IPv6:** `fe80::3fef:360c:304:64e%5`

> IPv4 uses 32-bit addresses, while IPv6 uses 128-bit addresses.

#### Loopback Addresses

Allow a computer to communicate with itself.

| Address | Type |
|---------|------|
| `127.0.0.1` | IPv4 Loopback |
| `::1` | IPv6 Loopback |

```powershell
ping 127.0.0.1
```

> Tests the local TCP/IP stack.

#### PrefixLength

Specifies the number of bits used for the network prefix.

Example:
```
PrefixLength : 64
```
Indicates a 64-bit network prefix in an IPv6 address.

### 6. Get-NetIPConfiguration vs Get-NetIPAddress

| Get-NetIPConfiguration | Get-NetIPAddress |
|------------------------|------------------|
| Displays overall network configuration | Displays detailed IP address information |
| Shows DNS server information | Shows address family |
| Shows default gateway | Shows prefix length |
| Provides interface configuration | Provides address state |

> **Remember:**
> - Use `Get-NetIPConfiguration` to check network configuration
> - Use `Get-NetIPAddress` to inspect configured IP addresses

### 7. Important Commands Summary

| Cmdlet | Purpose |
|--------|---------|
| `Get-ComputerInfo` | Retrieves system information |
| `Get-LocalUser` | Lists local user accounts |
| `Get-NetIPConfiguration` | Displays network configuration |
| `Get-NetIPAddress` | Displays configured IP addresses |

### 8. PowerShell in Cybersecurity

- **System Investigation:** Identify the operating system and system configuration
- **User Investigation:** Check local user accounts and their enabled status
- **Network Investigation:** Identify IP addresses, DNS servers, and default gateways
- **Troubleshooting:** Understand network interface and IP configuration issues

### 9. Key Takeaways

- `Get-ComputerInfo` retrieves detailed system information
- `Get-LocalUser` lists local Windows accounts
- `Get-NetIPConfiguration` displays network configuration
- `Get-NetIPAddress` provides detailed IPv4 and IPv6 information
- `127.0.0.1` is the IPv4 loopback address
- `::1` is the IPv6 loopback address
- PowerShell helps administrators investigate and manage Windows systems

---

## Real-Time System Analysis in PowerShell

### Introduction

PowerShell provides several cmdlets for monitoring and investigating a Windows system in real time. These commands help security analysts inspect:

- Running processes
- Windows services
- Active TCP connections
- File hashes
- Alternate Data Streams (ADS)

They are useful in **system administration, troubleshooting, incident response, digital forensics, and threat hunting**.

### 1. Get-Process

Displays information about processes currently running on a Windows system. A **process** is an instance of a running program or application.

```powershell
# Display all running processes
Get-Process

# Find a process by name
Get-Process -Name chrome

# Find a process using its PID
Get-Process -Id 2340
```

**Important output columns:**

| Column | Description |
|--------|-------------|
| Handles | Number of handles opened by the process |
| NPM(K) | Non-paged memory usage in KB |
| PM(K) | Paged memory usage in KB |
| WS(K) | Working Set memory usage in KB |
| CPU(s) | Total CPU time used by the process |
| Id | Process ID (PID) |
| SI | Session ID |
| ProcessName | Name of the process |

#### What is a PID?

A **Process ID (PID)** is a numerical identifier assigned to a process by Windows. It helps identify and investigate a specific running process.

> **Security use case:** Analysts can inspect suspicious processes, identify their PIDs, and investigate unusual resource usage or process activity.

### 2. Get-Service

Displays information about Windows services and their current status. A **Windows service** is a background program that provides functionality to the operating system or other applications.

```powershell
# Display all services
Get-Service

# Check a specific service
Get-Service -Name Spooler

# Display only running services
Get-Service | Where-Object {$_.Status -eq "Running"}
```

**Important output columns:**

| Column | Description |
|--------|-------------|
| Status | Current service status |
| Name | Internal service name |
| DisplayName | Readable service name |

**Common service statuses:**
- **Running:** The service is currently running
- **Stopped:** The service is not currently running
- **Paused:** The service has been temporarily paused

> **Security use case:** Attackers may create or modify Windows services to maintain persistence. Analysts can inspect unusual services during incident response and threat hunting.

### 3. Get-NetTCPConnection

Displays TCP connection information, including local and remote endpoints.

```powershell
Get-NetTCPConnection
```

**Important output columns:**

| Column | Description |
|--------|-------------|
| LocalAddress | Local system IP address |
| LocalPort | Local TCP port |
| RemoteAddress | Remote system IP address |
| RemotePort | Remote TCP port |
| State | Current TCP connection state |
| AppliedSetting | Applied TCP connection settings |
| OwningProcess | PID of the process associated with the connection |

**Common TCP states:**

| State | Description |
|-------|-------------|
| Listen | Waiting for incoming TCP connections |
| Established | TCP connection is established |
| TimeWait | Connection has closed and is waiting before final cleanup |

**Understanding listening addresses:**
- `0.0.0.0` generally represents all available IPv4 interfaces when used as a local listening address
- `::` is the IPv6 unspecified address and generally represents all available IPv6 interfaces when listening

**Identifying the process behind a connection:**

```powershell
# Find the process using a PID
Get-Process -Id 1444
```

> **Security use case:** Analysts can investigate unexpected TCP connections, identify remote endpoints, and determine which process owns a connection.

> **Note:** `Get-NetTCPConnection` displays TCP connection information, not UDP connections.

### 4. Get-FileHash

Calculates a cryptographic hash for a file. A **hash** is a fixed-length value calculated from file content — used to verify file integrity and compare files.

```powershell
Get-FileHash -Path .\sample.exe
```

By default, PowerShell uses the **SHA256** algorithm. Specify an algorithm:

```powershell
Get-FileHash -Path .\sample.exe -Algorithm SHA256
Get-FileHash -Path .\sample.exe -Algorithm MD5
```

**Common uses:**
- Verify file integrity
- Identify known malicious files using threat-intelligence sources
- Detect changes in file content
- Support malware analysis and incident response

> **Security use case:** An analyst can calculate the SHA256 hash of a suspicious executable and compare it with known malware indicators.

### 5. Alternate Data Streams (ADS)

**Alternate Data Streams (ADS)** are a feature of the **NTFS file system** that allows additional named data streams to be associated with a file. An NTFS file normally has a default data stream containing its regular content. It can also have additional named streams.

**List all streams attached to a file:**

```powershell
Get-Item -Path "C:\Data\example.txt" -Stream *
```

**Understanding the output:**

A file may contain:

1. **Default Data Stream** — `:$DATA`
   - The normal data stream containing the regular file content
   - Not an alternate data stream

2. **Alternate Data Stream** — for example, `hiddeninfo`
   - An additional named stream attached to the file

**Conceptually:**

```
example.txt
    |
    |-- Default Data Stream (:$DATA)
    |
    |-- Alternate Data Stream (:hiddeninfo)
```

**Read an Alternate Data Stream:**

```powershell
Get-Content -Path "C:\Data\example.txt" -Stream hiddeninfo
```

> **Security use case:** Attackers may misuse ADS to hide data. Security analysts can inspect file streams during forensic investigations and threat hunting.

> **Important:** ADS also has legitimate uses. Finding an ADS does not automatically mean a file is malicious.

### Summary

| Cmdlet | Purpose |
|--------|---------|
| `Get-Process` | Displays running processes |
| `Get-Service` | Displays Windows services and their status |
| `Get-NetTCPConnection` | Displays TCP connections and listening endpoints |
| `Get-FileHash` | Calculates a file hash |
| `Get-Item -Stream *` | Lists streams attached to a file |
| `Get-Content -Stream` | Reads a named data stream |

### Practical Security Investigation Workflow

1. List running processes using `Get-Process`
2. Inspect unusual Windows services using `Get-Service`
3. Review TCP connections using `Get-NetTCPConnection`
4. Identify the process associated with a connection using its PID
5. Calculate the hash of a suspicious file using `Get-FileHash`
6. Inspect file streams using `Get-Item -Stream *`

> These commands provide useful information for Windows system analysis, incident response, digital forensics, and threat hunting.

---

## 📢 About Zero2NullSecurity

**Zero2NullSecurity** is a community-driven initiative providing **free, high-quality cybersecurity learning resources** for beginners and professionals alike.

- 📚 Free notes and guides
- 🛡️ Blue team, red team, and general security content
- 🎯 Practical, hands-on learning focus
- 🤝 Open to community contributions

If these notes helped you, consider ⭐ starring the repository and sharing it with others.

---

<p align="center">
  <b>Made with 🖤 by Zero2NullSecurity</b><br>
  <i>Zero to Null — Your Journey Starts Here</i>
</p>