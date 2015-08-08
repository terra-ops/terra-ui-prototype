# terra-ui-prototype

A drupal 7 site with the UI module (https://github.com/albatrossdigital/terra_ui) installed.

# Setup

Launch the site with terra.

```
terra app:add ui http://github.com/terra-ops/terra-ui-prototype

terra env:add ui local --enable
````
This launches a RabbitMQ container as well as the drupal stack.

Then run the "queue" command:

```
$ terra queue
```

This command defaults to using "local.computer" (IP 192.168.99.100) as the host of the rabbitMQ server.  If you are running it on a different server, use:

```
$ terra queue tcp://guest:guest@1.2.3.4:5672/terra
```

This command runs continuously, running queued commands the moment they hits the queue.


# Front End

Just a drupal7 site with this module: https://github.com/albatrossdigital/terra_ui

The drupal site has app nodes and environment nodes.

Create an app node and it will queue the command `app:add` in the rabbitMQ server.

Create an Environment, it will queue the `environment:add` command.

# Advantages

- Front end communicates via REST. Can be hosted anywhere, and in any language.
- Queue command runs from the same user and the same command line app as the rest of the terra commands.

This is basically the start of what aegir 4 could look like.
