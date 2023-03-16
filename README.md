# UE Capability Parser
> **Warning**
> Work In progress

UE Capability parser used by smartphonecombo.it and cacombos.com

```
$ java -jar uecapabilityparser.jar --help
usage: ueCapabilityParser
 -c,--csv <arg>            Output a csv, if no file specified the csv will
                           be output to standard output.
                           Some parsers output multiple CSVs, in these
                           cases "-LTE", "-NR", "-EN-DC", "-generic" will
                           be added before the extension.
 -d,--debug                Print debug info.
 -h,--help                 Print this help message.
 -i,--input <arg>          Main capability file.
 -inputENDC <arg>          ENDC UE Capability file.
 -inputNR <arg>            NR UE Capability file.
 -j,--compactJson <arg>    Output a Compact Json (used by
                           smartphonecombo.it), if no file specified the
                           json will be output to standard output.
 -l,--uelog <arg>          Output the uelog, if no file specified the
                           uelog will be output to standard output.
 -multi,--multiple0xB826   Use this option if input contains several
                           0xB826 hexdumps separated by blank lines and
                           optionally prefixed with "Payload :".
 -n,--newEngine            Use the new engine (default)
 -nr,--defaultNR           Main capability input is NR (otherwise LTE).
 -t,--type <arg>           Type of capability.
                           Valid values are:
                           H (UE Capability Hex Dump)
                           W (Wireshark UE Capability Information)
                           N (NSG UE Capability Information)
                           P (CellularPro UE Capability Information)
                           C (Carrier policy)
                           CNR (NR Cap Prune)
                           E (28874 nvitem binary, decompressed)
                           Q (QCAT 0xB0CD)
                           QNR (0xB826 hexdump)
                           M (MEDIATEK CA_COMB_INFO)
                           O (OSIX UE Capability Information).
 -T,--TsharkPath <arg>     Set tshark path. (Tshark is used for H type)
```

## Run in Docker

Create data directory and place log files in directory. This directory will be mounted inside of the container.

```bash
$ mkdir data
$ docker run -it --rm -v ${PWD}/data:/home/java ghcr.io/HandyMenny/uecapabilityparser
```

Example:

```bash
$ docker run -it --rm -v ${PWD}/data:/home/java ghcr.io/handymenny/uecapabilityparser:main -t H -i "uecapability.txt" --multi -c uecapability-parsed.txt
```

## Run in locally

Install latest Java 1.8 or newer and download latest release from Release page.

```bash
$ java -jar uecapabilityparser.jar
```
