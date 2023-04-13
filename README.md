# tftarget

Script to make easier the need to use targets in terraform, when launching tftarget in a terraform folder, apart from the normal output of terraform, the script returns something like this:

![Report](https://github.com/smorenodp/tftarget/blob/main/images/report.png)

Each line corresponds with one resource that exists in the terraform report, the green one are the ones being created, the yellow ones the updated and the red ones the deleted (this is also explained next to the resource). The first thing we see in the line is a number, this is the id of the resource and the value used when referencing it in when selecting resources for the target command. There are 3 ways to reference them:

* <number> -> to reference a resource directly
* <number>-<number> -> to reference a sequence of resources
* !<number> -> to reference a resource to NOT be in the terraform command

This are some examples:

`1-3` -> Create a terraform command with the first 3 resources

`!2` -> Create a terraform command with all the resources except the second one

`1-10,!7` -> Create a terraform command with the first 10 resources except the seventh one

`1,2,4,5` -> Create a terraform command with the first, second, fourth and fiveth resources



There are some tags we can send when launching the tftarget to modify it's behaviour:

* -plan -> (the default behaviour) the command generated is terraform plan
* -apply -> the command generated is terraform apply
* -v -> send a var-file for the command
* -prefix -> use a prefix to filter the resources and only show the ones that correspond with it
* -cache -> cache the plan to use in future tftarget executions (mostly use for debug)
* -all -> select all resources and don't ask to select in the list
* -y -> don't ask for user feedback and launch the command directly
* -q -> quiet mode, don't show terraform output



