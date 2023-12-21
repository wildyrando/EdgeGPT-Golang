# EdgeGPT-Golang
Modified Version from https://github.com/billikeu/Go-EdgeGPT


```golang
package main

import (
	"log"

	EdgeGPT "github.com/wildyrando/EdgeGPT-Golang/Resources"
)

func callback(answer *EdgeGPT.Answer) {
	if answer.IsDone() {
		log.Println(answer.NumUserMessages(), answer.MaxNumUserMessages(), answer.Text())
	}
}

func main() {
	log.SetFlags(log.LstdFlags | log.Lshortfile)
	bot := EdgeGPT.NewChatBot("config.json", []map[string]interface{}{}) // proxy deleted
	err := bot.Init()
	if err != nil {
		panic(err)
	}
	err = bot.Ask("give me a joke", EdgeGPT.Creative, callback)
	if err != nil {
		panic(err)
	}
	err = bot.Ask("It's not funny", EdgeGPT.Creative, callback)
	if err != nil {
		panic(err)
	}
}

```
