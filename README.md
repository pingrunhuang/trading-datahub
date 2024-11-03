# crypto-trading-bot
This is a module that used to fetch historical market data from various 
exchanges using http request.


## setup

```
python -m pip install venv
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```
1. clone another repository `trading-meta` 
2. save the path of the previous step and add it into `python.analysis.extraPaths` in the .vscode/settings.json file.


once setup virtual environment, we can run follows:
`python main.py --funcname upsert_symbols` this is update all the symbols for all exchanges specified in the config file

`python main.py --funcname grab_klines`

## design 
the `connections` module is where I store all the connections to different exchanges
I define a base connection class which has all the common functions that one connection is supposed to have.
For example, 
each connection will have a symbol manager which allows it to query all the symbols' info into memory
each connection should have a union way to write data into databases
The project use async http request and async data writing into database for faster runtime.


### different functionalities
- bar data grabbing
- trades grabbing
- securities data grabbing
- minnor operations
each functionality will have one corresponding config file to that

## how does it work?
define the config file in the `configs` directory as shown in the example configurations
