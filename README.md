# The Telegram Toolkit: a tool to enrich Telegram data

## Description

Telegram channels are public broadcast channels on the Telegram messaging platform where creators can share messages, media, and updates with a large audience. Users can join channels to receive notifications and access content posted by the channel administrators, making it an effective tool for disseminating information to a wide audience. The Telegram Toolkit is a powerful software designed to enhance collected Telegram data by uncovering implicit information not directly available through the platform. It facilitates tasks such as revealing connections between channels and creating message-forwarding chains, providing users with valuable insights and analysis capabilities.

The Telegram Toolkit provides the following functionalities:

1. *Entities in Telegram*. Entities are provided only using text span indexes; the Telegram Toolkit extracts them.

2. *Channel to channel graph*. Given the collected data, it creates a channel-to-channel graph where nodes are the channels and edges are built when a message is forwarded from a channel (source) to a destination channel. This functionality creates a graph in [GML format](https://networkx.org/documentation/stable/reference/readwrite/gml.html). The edges are associated with the times when messages are forwarded.

3. *Message chain generation*. When you post a message and someone re-posts or forwards it, you can usually see where and when the message is forwarded. This does not happen with Telegram messages. As a solution, this functionality creates a CSV file where each source message (i.e., a new message) is associated at least with one destination message (i.e., forwarded message), the forwarding time, and the message text. Messages that are never forwarded do not appear in the CSV. The user must note that the source message and its channel might not be contained in the input collection of data; this is because Telegram does not provide information about where a message is forwarded and the proposed generation uses a backward mechanism starting from the destination messages.


**Note**: This tool is under active development, and new functionalities will be continuously added. If you have ideas for features that would enhance your research experience, please open an issue to share your suggestions with the MH Team. We'll carefully review each proposal to determine feasibility and prioritize implementation. Thank you for exploring our tool!

## Keywords
Entity Detection, Graph Generation, Information Spread.

## Relevant research questions that could be addressed with the help of this method 

The Telegram Toolkit is designed to provide enriched data and features to address research questions like:

  1. *Information Flow Analysis*: How does the use of the Telegram channel graph and entities enhance our understanding of information dissemination patterns within and across Telegram channels?

  2. *Network Analysis*: What insights can be gained from analyzing the network structure of Telegram channels and their connections using the features provided by the Telegram Toolkit?

  3. *Content Analysis*: How does the content shared across Telegram channels evolve over time, and how can entities assist in identifying trends, biases, and influential content creators?

  4. *Audience Engagement*: To what extent does audience engagement, measured by factors such as message forwarding chains and user interaction, contribute to the success and longevity of Telegram channels?

  5. *Community Structure and Boundary Formation*: How do the structures of message forwarding networks, uncovered by the TelegramToolkit, inform our understanding of community boundaries, subgroup formations, and the processes of inclusion and exclusion within Telegram ecosystems, and what implications do these dynamics have for social cohesion and identity formation?

  6. *Disinformation and Misinformation*: How can the tracking of message propagation pathways assist in unraveling the dynamics of misinformation dissemination, rumor amplification, and collective sensemaking processes within Telegram channels, and what strategies can be devised to foster critical thinking and information literacy in online communities?

### Social Science Usecase

*Use case 1:* Upon finding the Telegram Toolkit in the Methods Hub, John explores its features and capabilities. He discovers functionalities such as entity identification and message chain generation, which are relevant to his research on disinformation in Telegram channels. John obtains a dataset of messages collected from Telegram channels using appropriate data collection methods. He ensures that the dataset covers the relevant period corresponding to the US Presidential Elections and contains messages from channels known for spreading political information and disinformation. John imports the collected dataset into the Telegram Toolkit for analysis. He verifies the integrity and format of the data to ensure compatibility with the Toolkit's processing algorithms. Using the Toolkit's entity identification feature, John identifies key entities related to the Presidential Elections within the dataset. Then, he creates the message chains; now he can investigate how disinformation propagates through message forwarding chains and explores the dynamics of information diffusion within the network.

*Use case 2:* Sarah designs her research study to explore the social dynamics within Telegram communities, focusing on the role of message-forwarding networks in shaping community boundaries and subgroup formations. Sarah collects a dataset of messages from a diverse range of Telegram channels representing various communities and topics of interest. She ensures that the dataset covers a sufficient period to capture the evolution of community dynamics. Sarah uses the Telegram Toolkit to extract the channel-to-channel graph. She can now identify central nodes, clusters, and subgroups within the networks to understand how information flows and circulates within the communities.


## Structure

- *data/* contains sample data composed of different files. Each file contains messages from a specific channel.

- *sample_output_entities/* and *sample_output/* contain sample output dataset as described below.

- *TelegramToolkit.py* contains the source code of the toolkit that implements the *TelegramToolkit* and *TelegramMessage* classes devised to perform the tool functions.

- *requirements.txt* the requirements necessary to use the Telegram Toolkit. 


## How to Use

1. Install the requirements by running ```pip install -r requirements.txt```

2. Use ```TelegramToolkit.py [-h] [-i INPUT_DATA_DIR] [-o OUTPUT_DATA_DIR] [-re] [-ccg] [-cmc] [-gn GRAPH_NAME] [-mcn MESSAGE_CHAIN_NAME ```

The description of the parameters is:
```

Telegram Toolkit Commands

options:
  -h, --help            show this help message and exit
  -i INPUT_DATA_DIR, --input-data-dir INPUT_DATA_DIR
                        The input directory containing raw data from Telegram. Default: 'data/'
  -o OUTPUT_DATA_DIR, --output-data-dir OUTPUT_DATA_DIR
                        The output directory where there results will be saved. Default: 'out/'
  -re, --resolve-entities
                        Resolve the entities in the raw Telegram data collection.
  -ccg, --create-channel-graph
                        Create the channel-to-channel graph from the Telegram data collection.
  -cmc, --create-message-chain
                        Create the message chains of the messages from the Telegram data collection.
  -gn GRAPH_NAME, --graph-name GRAPH_NAME
                        Name of the graph created using the '-ccg' or '--create-channel-graph' option. Default: mygraph
  -mcn MESSAGE_CHAIN_NAME, --message-chain-name MESSAGE_CHAIN_NAME
                        Name of the CSV file containing the information to which channels a message was forwarded to. It only works with either '-cmc' or '--create-
                        message-chain' option. Default: my_message_chain

```

### Input data

A data sample is available with this repository under *data/*.

If interested the user can feed the TelegramToolkit with the data collected by [TelegramDataCollector]() [In development]



### Sample Input to the method

Please explore *data/*.


### Sample Output of the method

A sample output (using the data under *data/*) is made available with this repository.

- *sample_output_entities/* contains all the messages with their entities that have been made explicit.

- *sample_output/* contains:

  - *mygraph.gml* the channel-to-channel graph with information about the times a destination channel posted a message from a source channel.

  - *my_message_chain.csv* the CSV file containing information about the *source message id*, *source channel id*, *destination message id*, *destination channel id*, *time*, and *message text*.


### Limitation

The Telegram Toolkit is designed to work with .jsonl files where each line of a file represents a [Telegram message as described by the Telethon API](https://tl.telethon.dev/constructors/message.html). 


## Contact
danilo.dessi@gesis.org


## Publication 
The Telegram Toolkit is still being developed. Details about publications will be added later in time.


  
  
 
 
 
