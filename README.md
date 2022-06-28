import React from 'react'
import {
    View,
    StyleSheet,
    SafeAreaView,
    StatusBar,
    Image,
    Text,
    Pressable,
    Linking, 

} from 'react-native';

const githubColor = '#010409'
const imageProfileGitHub = 'https://avatars.githubusercontent.com/u/101408372?v=4'
const urlToMyGitHub = 'https://github.com/guimaraesadev';

const colorLightGitHub = '#C9D1D9';
const colorDarkGitHub = '#bcb8b6'
const DarkSlateGray = '#030201'

const App = () => {

    const handlePressGoToGitHub = async () => {
        console.log('Verificando link!');
        const res = await Linking.canOpenURL(urlToMyGitHub)
        if (res) {
            console.log("Link aprovado")
            console.log("Abrindo link!")
         await Linking.openURL(urlToMyGitHub)
        }
    }


    return (
        
        <SafeAreaView style={style.container}> 
        
            <StatusBar backgroundColor={githubColor} barStyle="light-content" />
            {/* configura a barra do lado de cima do telefone */}

        <View style={style.content}>
                <Image
                    style={style.avatar}
                    source={{ uri: imageProfileGitHub }}
                    accessibilityLabel="Avatar de Sabrina Guimarães"
                />
                
                <Text style={[style.defaultText, style.name]}>Sabrina Guimarães</Text>
                <Text style={[style.defaultText, style.nickname]}>@guimaraesadev</Text>
                <Text style={[style.defaultText, style.description]}>Full Stack Developer. From Brazil.</Text>

                <Pressable onPress={handlePressGoToGitHub}> 
                    {/* está funcionando => quando clica no botão aparece no console.log */}

                <View style={style.button}>
                    <Text style={style.defaultTextButton}>
                        Open GitHub
                    </Text>
                </View>
                
                </Pressable>


        </View>
    
        </SafeAreaView>
    );
};

export default App;

const style = StyleSheet.create({
    container: {
        backgroundColor: githubColor, 
        flex: 1, // pegue o tamanho total da tela e expanda esse estilo. 
        justifyContent: 'center',
        alignItems:'center'
    },
    content: {
        alignItems: 'center',
        padding: 20,
    },
    avatar: {
        height: 250,
        width: 250,
        borderRadius: 100,
    },
    defaultText: {
        color: 'white'
    },
    name: {
        marginTop: 20,
        fontSize: 24,
    },
    nickname: {
        fontSize: 20, 
        color: colorLightGitHub
    },
    description: {
        fontSize: 19,
        fontWeight: 'bold'
    },
    button: {
        marginTop: 20,
        backgroundColor: colorDarkGitHub,
        borderRadius: 18,
        padding: 10
    },

    defaultTextButton: {
        color: DarkSlateGray,
        fontSize: 15,
        fontWeight: 'bold'
    }
});
