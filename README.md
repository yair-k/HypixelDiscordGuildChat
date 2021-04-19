# Hypixel Discord Chat Bridge

A two-way chat bridge between [Hypixel](https://hypixel.net/) guild chat and a [Discord](https://discord.com/) channel. The application utilizes [Discord.js-light](https://github.com/timotejroiko/discord.js-light) for communicating with Discord, and [Mineflayer](https://github.com/PrismarineJS/mineflayer) for communicating with Hypixel.

> This application will login to Hypixel using Mineflayer which is not a normal Minecraft client, this shouldn't affect bans or logs but if you have many IP's logged on the server (VPN's and such), be carefull to not risk a 30 day security ban (appealable). 

> BY USING THIS PROGRAM, YOU TAKE FULL RESPONSIBILITY OF YOUR MINECRAFT ACCOUNT. THE CREATOR IS NOT RESPONSIBLE TO ANY MISTAKES YOU MAKE. USE WITH CAUTION.

<hr>


## Table of Content
- [Prerequisites](#prerequisites)
- [Setup Guide](#setup-guide)
- [Configuration](#configuration)
- [Roadmap](#roadmap)

### Prerequisites

- NodeJS >= 14 (https://nodejs.org/en/download/)
- Yarn >= 1.2 (https://classic.yarnpkg.com/en/docs/install/#windows-stable)
- A Premium Minecraft account (NFA works)

### Setup Guide

To get started, download and extract the source code onto your main place

    https://github.com/yair-k/HypixelDiscordGuildChat/releases/download/1.0/HypixelDiscordGuildChat.zip

Next open CMD and go into the `HypixelDiscordGuildChat` Folder wherever you installed it. Or you can use File explorer and enter `cmd` on the search bar to open the directory directly.

    cd desktop
    cd HypixelDiscordGuildChat
               OR
    cmd (in search bar of File Explorer)

In CMD, install all the dependencies using Yarn.

    yarn

While the dependencies are being installed you can edit the configuration file (`config.json`) with the help of the example one

    config.example.json:config.json

Once you're done all that, you can run the program.

    node index.js

#### Minecraft

The minecraft section includes a `username` and `password` option, if using a Mojang account these should be filled out with your Mojang username and password for the Minecraft account you plan on using, your Minecraft username is most likely the email it was created with. If using with a microsoft account change `accountType` to `microsoft`, `username` and `password` are not required and will be left blank as you will be directed to the [Microsoft Link page](https://www.microsoft.com/link). There is also a `lobbyHolder` option which is used in the `!guildlobby` command, this command will whisper the user specified in the config with a message using the `?tw <username>` format, for this command to do anything another bot needs to listen, and then act when receiving the message.

#### Discord

The Discord options includes the `token`, `channel`, `commandRole`, `ownerId`, and `prefix` options.

The token is the Discord application token, if you don't already have a Discord App, you can [create a new app](https://discordapp.com/developers), then convert the app to a Discord bot, and then get your Discord bot token on the "Bot" page.

The Discord channel is the ID of the text channel the bot should be linked with, the bot will only send and listen to messages in the channel defined in the config.

The command role is the ID of any role on the server the bot is hosted for, any user with the role will be able to run all the Discord commands built into the bot, like `!kick` and `!relog`.

> Note: Any user can run the `!help` command, however all the other commands requires the user has the command role.

The owner ID is similar to the command role, however this is the ID of the user that should have full access to the `!override` command, the user with this permission can use the command to run virtually any command via the bot, and should therefore be limited to just the owner of the bot.

The prefix is the command prefixed used for all the commands in the bot on the Discord side, by default this is set it `!`.

### Commands

<> = Required arguments, [] Optional arguments
!help - Displays this command list (!h)
!relog [delay] - Relogs the MC client, a delay can be given in seconds, if no delay is given it will default to 5 seconds (!r)
!override <command> [args] - Executes the string attached. This is a dangerous permission to grant (!o, !or)
!invite <player> - Invites the specified user to the guild, providing the guild isn't full (!i, !inv)
!kick <user> [reason] - Kicks the specified user from the guild (!k)
!promote <user> - Promotes the specified user by 1 rank (!p, !up)
!demote <user> - Demotes the specified user by 1 rank (!d, !down)

### Roadmap

- [ ] Chat message filter
  - The filter should block any messages sent from Discord to Hypixel that contains banable words, and words that could potentially cause a mute.
- [ ] Log guild joins & leaves
  - Send a message in Discord when people join or leave the guild, and when people login or logout of Hypixel.
- [ ] Send Discord message when the bot comes online and offline
  - `Bridge bot is online`, `Bridge bot is offline`
- [ ] Add support for officer chat
  - Allocate a second discord channel to use for two way officer chat.
